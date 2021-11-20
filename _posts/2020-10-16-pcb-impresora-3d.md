---
layout: post
title: Insolado de PCB con impresora 3D DLP
subtitle: Una 35 mm todoterreno
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [proyectos]
---

A principios del año pasado tuve que diseñar un pequeño circuito electrónico de ampliación de señales mioeléctricas. Aunque existen un gran número de empresas que fabrican PCB con un acabado estupendo y a bajo coste, yo no contaba con el tiempo que requería el envío. Por lo que mi única opción era fabricar la PCB yo mismo.

Ya había fabricado placas con anterioridad, pero en esta ocasión no contaba con una insoladora. Por suerte, un amigo disponía de una impresora 3D DLP y me la ofreció para que intentara usarla como sustituto de la insoladora. Pensamos que, si la pantalla de la impresora podía curar resina, también debería poder exponer la placa.

En su momento no encontré casi ninguna información sobre este método, así que aprovecho para documentar mi experiencia (aunque sea con casi 2 años de retraso) por si a alguien le resulta de utilidad.

<img src="{{ 'assets/img/pcb_schematic.jpg' | relative_url }}" alt="Esquemático del PCB a insolar" />

## La impresora Photon de Anycubic

Las impresoras 3D DLP (Direct Light Processing) son aquellas que obtienen la pieza deseada a partir de un baño de resina fotosensible que se cura capa a capa mediante una pantalla de proyección digital.

Estas impresoras descienden directamente de las SLA (las primeras impresoras 3D que se concibieron), que utilizan un único haz laser junto a juego de espejos para ir curando los diferentes puntos que formarán parte de la pieza. Las DLP, en cambio, pueden curar al mismo tiempo todos los puntos de una capa.

La impresora que utilicé para este experimento fue la [Photon de Anycubic](https://www.anycubic.com/products/anycubic-photon-3d-printer). Esta impresora cuenta con una pantalla LCD de resolución 2K (2560×1440), lo cual supone un nivel de detalle excelente para exponer una PCB. Este modelo y su versión mejorada son muy populares entre la comunidad maker debido a su bajo coste.
Impresora DLP Photon

## Preparando el STL

Para fabricar una PCB de forma correcta, debemos conservar el recubrimiento fotosensible únicamente en las pistas y pads. De esta forma, estas zonas quedarán protegidas del ataque del ácido que actuará en el resto de la placa.

La forma más sencilla que se me ocurrió para «engañar» a la impresora fue realizar una pieza extruyendo el negativo de la placa.

En primer lugar, debemos obtener una imagen plana de nuestro circuito desde el programa que hayamos usado para diseñarlo. Para invertir los colores de esta imagen recomiendo usar [Inkscape](https://inkscape.org/), un editor de gráficos vectoriales de código abierto.

Una vez obtenido el negativo de nuestra placa, lo exportamos en formato SVG. Por último, importamos este archivo a nuestro programa de diseño 3D favorito y lo extruimos.

<img src="{{ 'assets/img/pcb_stl.jpg' | relative_url }}" alt="STL de la imagen del PCB invertida" />

Las impresoras Photon cuentan con su propio slicer (el programa usado para generar el G-code) que se puede descargar gratuitamente desde su web. Este programa nos deja configurar (entre otros muchos parámetros) el tiempo de exposición de la capa inferior, por lo que podemos ajustarlo según nos convenga.

Utilicé unos trozos de cinta para marcar la posición de la placa en la pantalla y, así, asegurarme que la colocaba correctamente.

<img src="{{ 'assets/img/photon_lcd.jpg' | relative_url }}" alt="Pantalla LCD de la impresora Photon" />

## Obteniendo la placa

Al no estar seguro del tiempo apropiado de exposición para la placa, corté varios pedazos para hacer pruebas. Creo que acabé usando un tiempo entre 7 y 12 minutos.

<img src="{{ 'assets/img/pcb_pruebas_tiempo.jpg' | relative_url }}" alt="Trozos de PCB para pruebas />

Una vez expuesta la placa, ya se puede seguir con el procedimiento habitual. Tendremos que revelar el circuito usando sosa caústica y, luego, atacarlo con el ácido   

<img src="{{ 'assets/img/pcb_revelado.jpg' | relative_url }}" alt="PCB revelado />                                                                        

Por último, solo queda hacer los taladros para los componentes.

<img src="{{ 'assets/img/pcb_taladro.jpg' | relative_url }}" alt="PCB con taladro /> 

