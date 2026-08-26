---
layout: post
title: "Exprimir una RTX 5060 Ti de 16 GB: auditoría de rendimiento y arquitectura de inferencia"
date: 2026-09-16
categories: [infraestructura, inteligencia-artificial]
tags: [hardware, vram, llama-cpp, benchmark, optimizacion]
---

# Exprimir una RTX 5060 Ti de 16 GB: auditoría de rendimiento y arquitectura de inferencia

Empiezo directamente con el problema técnico central que solemos encontrar en las auditorías de infraestructura. La inmensa mayoría de los equipos técnicos e ingenieros de plataforma asumen de forma dogmática que ejecutar un modelo paramétrico masivo requiere clústeres de inferencia de gama alta o el alquiler de instancias con múltiples aceleradores en la nube. La realidad operativa demuestra que una infraestructura baremetal bien afinada sobre hardware de consumo puede ofrecer latencias de producción estables, siempre y cuando se audite y optimice cada capa de la pila tecnológica con rigor absoluto.

En este análisis vamos a diseccionar el rendimiento empírico de un nodo local dedicado a la inteligencia artificial, operando sobre una instalación mínima de Ubuntu Server 26.04 LTS. La base de hardware consta de un procesador Intel Core i5 montado sobre una placa base Gigabyte B760M DS3H DDR4 de revisión 1.0, acompañado de una única tarjeta NVIDIA GeForce RTX 5060 Ti de 16 GB. El objetivo de este documento no es publicitar ni validar los componentes seleccionados, sino demostrar analíticamente cómo la configuración estricta del enrutador y del motor de inferencia determina el éxito o el fracaso absoluto de un despliegue de esta naturaleza.

El error de diseño más común en la industria actual es desplegar contenedores opacos, abstraer las dependencias y utilizar configuraciones por defecto que desperdician ciclos de reloj. En nuestro caso, la decisión arquitectónica ha sido prescindir de capas intermedias, ejecutando el binario del servidor de inferencia de forma nativa. Esto nos permite controlar el enrutamiento de los modelos mediante un archivo de configuración centralizado y estructurado que expone, sin filtros, la parametrización exacta de la asignación de memoria y el cálculo de la atención.

```ini
# Presets de modelos para llama-server (modo router)
# Cada sección define un modelo. El cliente selecciona por "model" usando
# el nombre de la sección o los alias definidos en la clave "alias".

[qwen36-A3B-IQ3]
model = /home/sico/modelos/Qwen3.6-35B-A3B-UD-IQ3_S.gguf
alias = qwen36-A3B-IQ3
ctx-size = 200000
device = CUDA0
split-mode = none
flash-attn = on
kv-offload = on
op-offload = on
repack = on
mmap = on
warmup = on
cont-batching = on
cache-type-k = q8_0
cache-type-v = q8_0
cache-ram = 0
threads = 4
threads-batch = 4
batch-size = 512
ubatch-size = 128
parallel = 1
fit = on
no-host = on
temp = 0.7
top-p = 0.8
top-k = 20
repeat-penalty = 1.05
reasoning = auto
jinja = on
prio = 2
prio-batch = 2
poll = 50
poll-batch = 1

[gemma4-26B-A4B-QAT-Q4]
model = /home/sico/modelos/gemma-4-26B-A4B-it-qat-UD-Q4_K_XL.gguf
alias = gemma4-26B-A4B-QAT-Q4
ctx-size = 200000
device = CUDA0
split-mode = none
flash-attn = on
kv-offload = on
op-offload = on
repack = on
mmap = on
warmup = on
cont-batching = on
cache-type-k = q8_0
cache-type-v = q8_0
cache-ram = 0
threads = 4
threads-batch = 4
batch-size = 512
ubatch-size = 128
parallel = 1
jinja = on
chat-template-file = /home/sico/modelos/chat_template.jinja
fit = on
no-host = on
temp = 0.7
top-p = 0.8
top-k = 20
repeat-penalty = 1.05
prio = 2
prio-batch = 2
poll = 50
poll-batch = 1

```

Al auditar este fichero de configuración, destaco de inmediato varias decisiones críticas de diseño que denotan un conocimiento profundo de la arquitectura de hardware subyacente. La directiva de forzar la variable de memoria en RAM a cero bloquea de raíz cualquier intento del motor de derivar datos a la memoria del sistema. En entornos de inferencia estricta, recurrir a la memoria del procesador a través del bus PCIe destruye por completo el rendimiento de generación, elevando la latencia a niveles inaceptables. Todo dato computacional debe permanecer confinado en la memoria de la GPU.

Adicionalmente, fijar la caché de claves y valores a una cuantización de ocho bits asegura que el modelo retenga la coherencia lógica en contextos de conversación o análisis documental extremadamente largos. Reducir drásticamente este valor degradaría la retentiva y precisión del agente, mientras que aumentarlo a parámetros sin compresión saturaría los dieciséis gigabytes de VRAM disponibles de forma prematura. El uso concurrente de la directiva de empaquetado continuo y el tamaño dinámico del contexto demuestran una estrategia de asignación elástica donde el motor escala milimétricamente el consumo de memoria sin provocar volcados por agotamiento de recursos.

Mención aparte merece la integración estricta de plantillas externas para estructurar el formato de interacción. Remplazar las secuencias genéricas embebidas por un fichero Jinja actualizado y específicamente diseñado para la llamada a herramientas corrige deficiencias críticas de parseo estructural. Cuando el modelo opera como el núcleo cognitivo de un agente orquestador, fallar en la generación de sintaxis JSON o alterar las etiquetas de detención invalida todo el flujo de trabajo automatizado, convirtiendo un error de formato en una caída crítica del servicio.

Pasando de la revisión pasiva a la instanciación del servicio en caliente, el registro de arranque por línea de comandos revela el nivel de agresividad en la gestión de la cola gráfica.

```bash
llama-server \
  --alias gemma4:26b-a4b-it-qat-q4_0,gemma4 \
  --host 0.0.0.0 \
  --port 8080 \
  --n-gpu-layers 999 \
  --ctx-size 98304 \
  --parallel 1 \
  --batch-size 1024 \
  --ubatch-size 256 \
  --threads 8 \
  --threads-batch 16 \
  --flash-attn on \
  --kv-offload \
  --op-offload \
  --repack \
  --mmap \
  --warmup \
  --cache-type-k q8_0 \
  --cache-type-v q8_0 \
  --cache-prompt \
  --cache-idle-slots \
  --cache-ram 4096 \
  --reasoning auto \
  --temp 0.7 \
  --top-p 0.95 \
  --top-k 40 \
  --min-p 0.0 \
  --repeat-penalty 1.05 \
  --prio 2 \
  --prio-batch 2 \
  --poll 50 \
  --poll-batch 1 \
  --threads-http 2

```

La instrucción de delegar novecientas noventa y nueve capas al acelerador garantiza matemáticamente que la CPU principal no intervenga en el cálculo tensorial pesado, limitando su función a tareas de orquestación de red y manejo de colas de entrada. Asimismo, la activación imperativa del cálculo de atención optimizada (Flash Attention) permite comprimir el escalado de consumo de memoria geométrica a medida que los tokens se acumulan en el historial. Sin forzar esta directiva, los cuellos de botella en la gráfica se harían insostenibles a partir de los primeros miles de tokens procesados.

La asignación de hilos del sistema en este script de inicio muestra variaciones respecto al perfil del enrutador, forzando ocho hilos para la generación de la unidad central y dieciséis para la fase de procesamiento masivo. Estas cifras son completamente coherentes para saturar la capacidad de los núcleos del procesador base sin llegar a provocar bloqueos o asfixiar los demonios críticos que sostienen el sistema operativo subyacente.

La prueba innegable de que esta arquitectura está balanceada no se construye sobre especulaciones lógicas, sino mediante la telemetría directa del hardware operando bajo estrés de producción. Monitorizando el subsistema PCIe y los sensores de la gráfica a través del panel oficial, extraemos una captura exacta del comportamiento físico frente a las directivas de software impuestas.

```bash
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 595.71.05              Driver Version: 595.71.05       CUDA Version: 13.2    |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 5060 Ti     Off |   00000000:01:00.0 Off |                  N/A |
|  0%   53C    P1            123W / 180W  |   15540MiB / 16311MiB  |     85%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0  N/A  N/A      18121      C   ...ama.cpp-cuda/bin/llama-server             15530MiB |
+-----------------------------------------------------------------------------------------+

```

La lectura técnica de este registro descarta cualquier debate infundado. Verificamos empíricamente una ocupación de memoria constante y sostenida en quince mil quinientos cuarenta megabytes. Operar el sistema con un margen de seguridad inferior a ochocientos megabytes de memoria de vídeo libre exige un perfilado de inferencia sumamente estricto; un solo bloque extra en el almacenamiento de contexto o un error en la cuantización de la caché provocaría un volcado de proceso inmediato. Estáis exigiendo el máximo límite físico del hardware sin comprometer la tolerancia a fallos.

Centrando el análisis en el apartado eléctrico y térmico, el sensor maestro reporta una demanda energética de ciento veintitrés vatios, cifra que se acomoda con amplísimo margen por debajo de la restricción estructural de ciento ochenta vatios. La temperatura estacionaria clavada en cincuenta y tres grados Celsius indica que la refrigeración es óptima y no existe ningún riesgo inminente de pérdida de rendimiento por estrangulamiento térmico preventivo. El ochenta y cinco por ciento de uso del procesador gráfico ratifica que el silicio ingiere información a gran ritmo, experimentando lógicas pausas de sincronización inherentes al diseño secuencial de los cálculos autorregresivos.

A pesar de que el indicador de uso gráfico avala la robustez de la parametrización, la verdadera prueba de fuego para un nodo destinado a asistir herramientas complejas no es su velocidad de impresión lineal, sino la eficiencia al digerir inyecciones masivas de texto. Al auditar un servidor que debe parsear historiales kilométricos de agentes de desarrollo, la velocidad de escritura pura cede toda la relevancia frente a la eficacia de la ingesta inicial.

```bash
Resultados principales:

Gemma4 26B.A4B Q4_0
Backend: CUDA
ngl: 999
KV: q8_0/q8_0
Flash Attention: on
batch: 1024
ubatch: 256
threads: 8

Bench:
pp512          2689.81 ± 19.55 t/s
tg128           121.26 ±  0.50 t/s
pp512+tg128     503.62 ±  1.24 t/s
pp2048+tg128   1142.60 ±  3.60 t/s
pp4096+tg256   1141.69 ±  1.08 t/s

```

Los resultados del banco de pruebas sintético validan contundentemente la arquitectura y castigan el dogmatismo. La velocidad de preprocesamiento puro eclipsa la marca de dos mil seiscientos ochenta y nueve tokens procesados cada segundo. Extrapolando este dato a un flujo operativo, significa que el sistema posee la fuerza bruta necesaria para leer, tokenizar y volcar un manual técnico extenso a su espacio latente en un lapso apenas superior a los tres segundos, dinamitando el principal vector de fricción en la construcción de arquitecturas de recuperación documental local.

Cuando simulamos una carga de trabajo mixta que combina la asimilación de un contexto exhaustivo y desencadena una generación elaborada, la plataforma se estabiliza de manera admirable superando la barrera de los mil cien tokens globales por segundo. En términos estrictos de decodificación token a token, la unidad de cálculo proyecta más de ciento veintiún fragmentos por segundo. Esta métrica de salida supera en múltiples factores la capacidad máxima de lectura humana, confirmando la solvencia total de la máquina para orquestar herramientas conversacionales síncronas.

El dictamen técnico tras cruzar estas telemetrías con los registros de arranque es innegociable. Resulta una negligencia operativa destinar presupuesto a migraciones compulsivas de hardware de tarjeta gráfica sin haber drenado previamente hasta la última gota de eficiencia ajustando los hiperparámetros de inferencia. La estabilidad que ofrece una plataforma afinada al milímetro, gestionada mediante configuraciones rígidas y auditada sin concesiones, desbanca sistemáticamente a clústeres infrautilizados que operan con directivas genéricas e indolencia técnica.

Tras diseccionar exhaustivamente estas métricas empíricas en relación con el coste del hardware, ¿consideráis rentable escalar vuestros nodos de servidor basándoos en corazonadas comerciales o estáis dispuestos a implementar protocolos estrictos de medición antes de firmar cualquier ampliación?
