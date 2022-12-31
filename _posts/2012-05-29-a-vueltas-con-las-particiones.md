---
layout: single
title: "A vueltas con las particiones"
date: "2012-05-29"
categories: linux
---

Tras un fallo de rendimiento en el MacMini , muy notable,tocaba investigar. Como indica el título era cosa de particiones. Exactamente es una perdida de alineación de particiones.

Lo normal es abordar este problema desde otro sistema operativo. Redimensionamos las particiones para corregir el desalineado.

**Mensaje:**

_WARNING: The partition is misaligned by 3072 bytes. This may result in very poor performance. Repartitioning is suggested._

He detectado el error desde la herramienta "utilidad de discos" de GNOME.

Benditas copias de seguridad , tras eliminar la tabla de particiones y generar una nueva no arranco el Grub y ni me permitía reinstalarlo.

Todo desde "cero" , Tocó generar nuevos sistemas de ficheros y una instalación limpia.
