---
layout: posts
title: "Recodificar pistas de audio con FFMPEG"
date: "2018-05-08"
categories: audio video
---

Actualmente tengo un chromecast y el sonido en AC3 y  DTS esta soportado.

**¿Pero de que manera ?** _Usando passthrough , así que si tu TV no es decodifica te quedas sin sonido._

**Solución:**

La opción más eficiente es re-codificar las pistas de audio a AAC , pero esto tiene un coste , el fichero queda estructurado de forma ineficiente para streaming. En este punto hubo que pasarse por la documentación de matroska, no sabia nada de esto , así que a mover neuronas un poco. Vamos  re-codificamos con FFMEG y optimizamos los ficheros para streaming con herramientas de matroska.

**Vamos a re-codificar**

Con el FFMPEG generaremos un fichero nuevo con todas sus pistas en las mismas posiciones y  las de audio procesadas , el resto (vídeo y subtítulos ) copiadas. Por si en un futuro tengo un equipo de audio con varios canales he preferido resamplear la pista de AAC a Dolby Prologic II en vez de mantener pistas y añadir nuevas. Esto es una elección personal , máxima información en el menor espacio posible

Para el resampleado utilicé esta [web:](https://superuser.com/questions/594741/how-to-use-ffmpeg-to-downmix-5-1-dts-hd-ma-or-dolby-truehd-to-stereo-aac-with-do)

\-af "aresample=matrix\_encoding=dplii"

Mapeo de pistas, [utilicé la wiki oficial](https://trac.ffmpeg.org/wiki/Map)

- \-map 0  Seleciona todas las pistas
- \-c:v copy  Copia las pista de vídeo sin codificar
- \-c:a aac    Codifica las pistas de audio en AAC
- \-c:s copy   Copia las pistas de subtitulos

Comando de ejemplo:

for %x in (\*.mkv) do ( ffmpeg.exe -i "%~x" -map 0 -c:v copy -c:a aac -af "aresample=matrix\_encoding=dplii" -c:s copy "%~nx\[AAC\].mkv")

**Nota**: el sistema de nombres "%~nx" devuelve el nombre sin extensión

Para asegurar el rendimiento en streaming utilizo la herramienta mkclean para estructurar el fichero de forma optima. Mas info en la [estructura del mkv](https://www.matroska.org/technical/order/index.html) y de la [herramienta](https://www.matroska.org/downloads/mkclean.html)

Comando de ejemplo:

for %x in (\*.mkv) do ( mkclean.exe --optimize "%~x" )

**Nota:** optimize **lleva dos guiones  "- - "**

Ejemplos:

for %x in (\*.mkv) do ( ffmpeg.exe -i "%~x" -map 0 -c:v copy -c:a aac -af "aresample=matrix\_encoding=dplii" -c:s copy "%~nx\_ENC.mkv")
