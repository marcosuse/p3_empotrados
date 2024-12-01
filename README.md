# Vending Machine Controller
## Descripción projecto
En este proyecto, se ha desarrollado un controlador para una máquina expendedora de café utilizando un Arduino junto con varios sensores y actuadores. La funcionalidad del proyecto está estructurada en diferentes estados dentro de un sketch. 
### FSM
El sketch principal sigue una logica de una FSM con diferentes estados ya que dentro de cada apartado de la practica se tienen que hacer diferentes cosas. No hace falta un esquema ya que el comportamiento es bastante sencillo.
### Hardware usado
Hemos usado esta lista de hardware:
  - Arduino UNO
  - LCD 16x2
  - Joystick
  - Sensor de Temperatura/Humedad DHT11
  - Sensor de Ultrasonidos (HC-SR04)
  - Botón
  - 2 LEDs normales (LED1, LED2)
y se conectan segun este diagrama:

[Fritzing]()
## Recursos usados 
En esta practica he usado diferentes recursos como threads, interrupciones y whatchdog.
### Threads 
Los ArduinoThreads son diferentes a los threads que usamos normalmente en un ordenador, estos unicamente nos ayudan a reducir el uso de millis para tareas que queremos que se ejecuten en un tiempo en concreto, por ejemplo si queremos que una tarea se ejecute cada 100 ms tendriamos que utilizar millis muchas veces para saber si se ha pasado el tiempo en el que tiene que ejecutarse.
En esta practica he usado los Threads para las lesturas de los sensores primarios quitando los botones ya que estos usan interrupciones y preferí ponerlos en el loop principal.
Usar los Threads en los sensores ayuda a evitar tener que llamar muchas veces innecesarias a los datos de los sensores, tambien ayuda que el codigo no se bloquee.
###
