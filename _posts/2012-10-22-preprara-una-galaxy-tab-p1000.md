---

title: "Preprara una Galaxy Tab P1000"
date: "2012-10-22"
categories: 
  - "sin-categoria"
---

Esto es un recordatorio de como preparar esta tablet con teléfono , utilizar un stockROM con un recovery y root.

## Buenas practicas

Debemos , **siempre** ,realizar una serie de limpiezas en cualquier dispositivo que vayamos a flashear. Eliminamos malos vicios de la ROM actual que pudieran afectar al funcionamiento de la nueva.

- wipe data/factory reset
- wipe cache partition
- wipe Dalvik Cache

Esto se debe realizar siempre antes de instalar cualquier ROM , no es necesario pero si recomendable antes de una intalación de recovery

## Flashear terminal

Lo básico es tener un Odín a mano , el mejor aliado para dispositivos Samsung. Necesitamos también la stockROM y el recovery , para este caso utilicé un ROM de TIM Mobile de versión 2.3.6 siendo esta la ultima versión que he encontrado por fecha de compilación y como revovery un CWM v3.0.0.5

Requisitos software

- El paso uno es instalar los drivers de Samsung , personalmente no me gusta el Kies así que con este paquete ya no te hace falta. (_**SAMSUNG\_USB\_Driver\_for\_Mobile\_Phones\_x86**_)
- La ROM a utilizar es _**SU-GT-P1000\_TIM\_1\_20120113135552**_
- El recovery _**CF-Root-TAB7\_XX\_OXA\_JQ1-v3.3-CWM3RFS**_
- Odín , yo he utilizado 1.85 pero como el terminal es viajo en casi todos los sitios utilizan la 1.75

 

 

Ahora deberemos de flashear el dispositivo varias veces , la rom y el recovery. Se utilizarán las misma opciones , simplemente cambiaremos el fichero cada vez

Opciones marcadas del Odín :

- Auto Reboot
- F. Reset Time
- El fichero se selecciona en PDA
    - P1000AIJQ1\_P1000XXJPZ\_P1000TIMJQ1\_HOME.tar.md5 (para la stockROM)
    - CF-Root-TAB7\_XX\_OXA\_JQ1-v3.3-CWM3RFS.tar (para el CWM)

![odin fin](images/5309342979_034353f6eb.jpg)

 

## Limpiar la stockROM
