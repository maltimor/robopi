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
uv4l --driver raspicam --auto-video_nr --width 320 --height 240 --encoding rgb565 --extension-presence=1 --framerate 30

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

Otra cosa: poner nodeJs
To Download via command line
* wget http://node-arm.herokuapp.com/node_latest_armhf.deb
* 
sudo dpkg -i node_latest_armhf.deb
# Check installation
node -v
5. Make it run on boot

This is the hardest part if you don't really know what you're doing.

You can define things to run on boot in /etc/rc.local. In that shell script, you don't have the same path as when you log in, so just running node app.js won't do the trick.

I tried a lot of different things that all gave errors like Illegal instruction or Permission denied or File not found.

What does work, is running one command as the default pi user. Because that user does have node in his path, the command is known.

su pi -c 'node /home/pi/server.js < /dev/null &'
I suggest using an absolute path to your Node.js-file just to make sure.


Bueno, parece que ya he instalado node, y tengo un servidor con socket.io que sirve una camara web y la relanza a los que se han conectado.



Ahora estoy con fgrab
necesita instalar zlib y libpng
# sudo apt-get install zlib-bin libpn-dev



