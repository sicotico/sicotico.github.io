---

title: "Particionar y Windows 7"
date: "2012-07-10"
categories: 
  - "sin-categoria"
---

No siempre tengo un Linux a mano , así que ha tocado recuperar un viejo disco desde Windows  7. El fdisk  ya no esta  y me ha ralentizado un poco . Renovarse o morir así que a buscar la nuevo utilidad ..... DISKPART .... lleva mucho con nosotros y ahora va a ser quien nos ayude. Su política de uso es una consola en la que para reducir problemas de mal uso  te obliga a seleccionar el dispositivo , partición o volumen donde quieres realizar la operación. Curioso sistema  ,  ejemplo:

LIST DISK

  Núm Disco  Estado      Tamaño   Disp     Din  Gpt
  ---------- ---------- ------- ------- --- ---
  Disco 0    En línea     232 GB  3072 KB
  Disco 1    En línea      15 GB      0 B
  Disco 2    En línea     149 GB      0 B

SELECT DISK 0

El disco 0 es ahora el disco seleccionado.

LIST PARTITION

 Núm Partición  Tipo              Tamaño   Desplazamiento
 ------------- ---------------- ------- ---------------
 Partición 1    Principal          155 GB    31 KB
 Partición 0    Extendido           76 GB   155 GB
 Partición 3    Lógico            3815 MB   155 GB
 Partición 4    Lógico              18 GB   159 GB
 Partición 5    Lógico              53 GB   177 GB
 Partición 2    Principal         1027 MB   231 GB

SELECT PARTITION "Numero de partición"

Ejemplo para volumen:

LIST VOLUMEN

  Núm Volumen Ltr  Etiqueta     Fs     Tipo        Tamaño   Estado     Info
  ----------- --- ----------- ----- ---------- ------- --------- --------
  Volumen 0     E                      DVD-ROM         0 B  Sin medio
  Volumen 1     G                      DVD-ROM         0 B  Sin medio
  Volumen 2     C               NTFS   Partición    155 GB  Correcto   Sistema
  Volumen 3     D   HP\_TOOLS    FAT32  Partición   1027 MB  Correcto
  Volumen 4     H   SD          NTFS   Extraíble     15 GB  Correcto
  Volumen 5                            Partición    149 GB  Correcto

SELECT "Numero de VOLUMEN"

Con la selección hecha ya podemos , borrarlo , verificar o lo que necesitemos.

 

Nota: Solo me ha hecho falta una vez en mi vida pero por si acaso lo dejo apuntado , s epeuden convertir disco de GPT (Mac) a MBR (PC) siempre que los discos estén vacíos.

Primero seleccionamos el disco , como indicamos antes y después ejecutamos la conversión

CONVERT MBR
