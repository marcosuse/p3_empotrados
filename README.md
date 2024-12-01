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
    
y se conectan segun el siguiente diagrama:

![Fritzing](Media/Untitled%20Sketch%202_bb.png)

## Recursos usados 
En esta practica he usado diferentes recursos como threads, interrupciones y whatchdog.
### Threads 
Los ArduinoThreads son diferentes a los threads que usamos normalmente en un ordenador, estos unicamente nos ayudan a reducir el uso de millis para tareas que queremos que se ejecuten en un tiempo en concreto, por ejemplo si queremos que una tarea se ejecute cada 100 ms tendriamos que utilizar millis muchas veces para saber si se ha pasado el tiempo en el que tiene que ejecutarse.
En esta practica he usado los Threads para las lesturas de los sensores primarios quitando los botones ya que estos usan interrupciones y preferí ponerlos en el loop principal.
Usar los Threads en los sensores ayuda a evitar tener que llamar muchas veces innecesarias a los datos de los sensores, tambien ayuda que el codigo no se bloquee.
### Interrupciones
las interrupciones las he usado para quitar quitar el ruido que tienen los botones ya que estos al pulsarlos y al dejar de pulsarlos crean ruido que se puede evitar con hardware o con software. 
Para quitar el ruido intente diferentes metodos pero llegue a la conclusion que el mas optimo es el mas sencillo, lo unico que hago es guardar el tiempo cuando el estado cambia y si cambia antes de un tiempo determinado, significa que eso ha sido ruido por lo que no contamos como si hubiese cambiado.
### Watchdog
la herramienta watchdog se basa en un timer que evita que el programa se quede bloquedo, y si se queda bloqueado vuelva a el inicio, yo lo he usado en el loop principal ya que si se bloquea sea donde sea quiero que vuelva a ejecutarse el programa ya que esto no deberia de ser admisible.

## Mejoras programa
En el enunciado de la practica no indica sobre el tiempo de servicio pero a mi me ha parecido algo antintuitivo que si detecta algo a menos de un metro se quede el programa esperando a que alguien le introduzca un cafe, por lo que yo he implementado dos formas para evitar esto.
  - la primera forma es que el sensor de ultrasonidos tambien tiene que detectar menos de un metro durante el los 5 segundos que se muestra la temperatura y humedad.
  - la segunda y ultima forma es que si cuando estas pidiendo el cafe tardas mas de 20 segundos en pedirlo volvera a el estado de esperando a la persona por que puede que hayas cambiado de opinion y te hayas ido.
## Video de el programa
[Multiple targets](https://urjc-my.sharepoint.com/:v:/g/personal/m_useros_2022_alumnos_urjc_es/EcKelRwQM0dKoAPLE8B15iEBTOkH20W0zGwYYBUda_o_lg?e=soFslA&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)
