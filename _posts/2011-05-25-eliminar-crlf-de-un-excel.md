---
layout: post
title: "Eliminar \"CRLF\" de un Excel"
date: "2011-05-25"
categories: dev
---

Desde el Excel

Selecciona las celdas yo elegí todo el excel Mientras mantienes presionada la tecla <Alt>, presiona la tecla <F11> Accedes al Microsoft Visual Basic para Aplicaciones

En la ventana que aparecerá, mientras mantienes presionada la tecla <Ctrl>, presiona la tecla <G>.

En la ventana "Inmediato" que verás, copia y pega el siguiente texto:

Selection.Replace Chr(10), Replacement:=" "

En "Remplacement" marcamos por que queremos sustituirlo , yo normalmente utilizo " . "

- Chr(13) =Salto de linea
- Chr(10) = Salto de carro

Presiona la tecla <Enter> , en la barra de titulo de la ventana veras fugazmente "ejecutándose" aparece escasos segundos

Todo esto para poder exportar un xls a csv , que por cierto tiene como norma una linea un registro ,así que no puede haber saltos en los registros.

Como nota dejo [aqui](https://www.surveygizmo.com/survey-support/tutorials/export-to-csv-from-office-spreadsheet-excel-calc-numbers/ "Exportar a CSV") como se exportar un xls a csv (CSV (delimitado por comas)(\*.csv))
