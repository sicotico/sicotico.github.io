---

title: "Cómo convertir un volumen FAT o FAT32 en NTFS"
date: "2007-11-06"
categories: 
  - "sin-categoria"
---

### 

**Nota** En mis pruebas no se han corropido datos , es recomendable realizar una copia de seguridad de los datos del volumen que desea convertir antes de iniciar la conversión.

Para convertir un volumen FAT o FAT32 existente en NTFS, siga estos pasos:

1. Abrimos un simbolo del sistema
2. Ejecutamos convert
    - Convert <Letra de la unidad a convertir> /fs:ntfs
    - Ejemplo: convert c: /fs:ntfs
3. Es nomral que te pida realizarlo en el proximo reinicio por no tener acceso en exclusividad al dispositivo
    - Porque sea la del sistema operativo , como en el ejemplo
    - Otros programas esten accediendo
