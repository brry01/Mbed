# Motor Control Code

Este archivo contiene el código para controlar un motor utilizando la biblioteca Mbed. A continuación se describe la funcionalidad del código y los pines utilizados.

## Descripción

El código controla el estado de un motor basado en las entradas de varios pines digitales. Además, utiliza cuatro LEDs para indicar diferentes estados del sistema.

## Pines Utilizados

- **Entradas Digitales:**
  - `start (p5)`: Botón de arranque.
  - `stop (p6)`: Botón de paro.
  - `guard (p7)`: Sensor de guardia (debe estar cerrado para operar).
  - `temp (p8)`: Sensor de temperatura (debe estar en un nivel seguro para operar).

- **Salidas Digitales:**
  - `led1 (p9)`: Indica si el sistema está listo.
  - `led2 (p10)`: Indica el estado del motor (encendido/apagado).
  - `led3 (p11)`: Indica si la guardia está abierta.
  - `led4 (p12)`: Indica si la temperatura es alta.

## Funcionalidad

1. **Inicialización:**
   - Se define un temporizador `blink_timer` para controlar el parpadeo del LED1 cuando el sistema no está listo.

2. **Bucle Principal:**
   - Se lee el estado actual de los sensores.
   - Se verifica si el sistema es seguro (`guard` cerrado y `temp` en nivel seguro).
   - Se verifica si el botón de paro está presionado.
   - Se controla el estado del motor:
     - Si el botón de arranque se presiona y el sistema es seguro, el motor se enciende.
     - Si el botón de paro se presiona o el sistema no es seguro, el motor se apaga.
   - Se actualizan los LEDs:
     - `led2` indica el estado del motor.
     - `led3` indica si la guardia está abierta.
     - `led4` indica si la temperatura es alta.
     - `led1` parpadea si el sistema no está listo, de lo contrario permanece encendido.

3. **Temporización:**
   - Se utiliza un temporizador para hacer parpadear `led1` si el sistema no está listo.

## Ejecución

El programa se ejecuta en un bucle infinito, verificando constantemente el estado de los sensores y actualizando los LEDs de acuerdo con las condiciones descritas.