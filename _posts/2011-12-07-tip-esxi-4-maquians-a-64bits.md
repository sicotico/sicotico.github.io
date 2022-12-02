---

title: "Tip: ESXi 4 (maquians a 64Bits)"
date: "2011-12-07"
categories: 
  - "sin-categoria"
---

Para habilitar el poder utilizar maquinas virtuales de 64 bits es un VMware ESX/ESXi  es necesario habilitar la tecnología propia de virtualización del procesador. En este caso un Inter Xeon se llama "Intel-VT technology"  y se habilita en BIOS

Nota: Para poder utilizar EVC (Enhanced VMotion Compability), la BIOS debe tener  "No-execute memory" habilitada.

Yo he realizado estos pasos desde la iLO

Acceder a la BIOS con la tecla F9 Opciones Avanzadas -> Processor Options -> Intel ® Virtualization Technology Elegir "Habilitar" Ya que estamos  podemos dejar 'No-Execute Memory Protection'  para tener VMware EVC Save and exit

Nota : Si tiene sun cluster , todos los nodos deben de tener la misma configuración de BIOS . ![](images/BIOS.JPG)
