robopi
======

Raspberry with MZTX-EXT-PI + Picamera/usb camera + 16FUN/LEDs to Control Robot


Requisitos de instalación
=========================

Comenzar con la Rasbian - wheezy

Bajar el modulo de yaolet, personalizar, modificar

Primer proceso: fb2lcd
instalar como modulo (TODO) ahora solo es un proceso que se ejecuta al principio.

Segundo proceso: picamera2fb
instalar v4l2 para raspberry, configurar /dev/video0 con los parametros que optimicen las converiones/tratamiento de la imagen
(actualmente RGB565 para todo: fb, lcd y picam)

Tercer proceso: hacer funcionar los 16 FUN LED's (i2c)
activar i2c
- blacklist
- modprobe
- /etc/modules

configurar herramientas i2c: http://lm-sensors.org
bajar utilidades
descomprimir en home/pi
compilar: make

ejecutar i2cdetect -y 0
ejecutar i2cset -y 0x60 0x06 X  (x=0 o 1)
pequeño esquema d eejemplo.


TODO
- adjuntar squema, y datasheets
- adjuntar imagenes de la mztx-ext-pi con pin out's

Cuarto proceso: poner todo junto y hacer funcionar el robot
de momento usar el teclado wireles para manejar el robot
hacer video



