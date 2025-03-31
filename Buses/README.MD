# Buses

Este archivo contiene un programa en C++ que utiliza la plataforma Mbed para leer el estado de un conjunto de interruptores y controlar un conjunto de LEDs en función del valor leído.

## Descripción del Código

El programa utiliza dos buses de E/S (`BusIn` y `BusOut`) para interactuar con los interruptores y los LEDs respectivamente.

- `BusIn switches(p5, p6, p7, p8);`: Define un bus de entrada con cuatro pines (p5, p6, p7, p8) para los interruptores.
- `BusOut leds(p9, p10, p11);`: Define un bus de salida con tres pines (p9, p10, p11) para los LEDs.

### Función Principal

La función `main()` contiene un bucle infinito que realiza las siguientes operaciones:

1. Lee el valor de los interruptores usando `switches.read()`.
2. Utiliza una declaración `switch` para asignar un valor a los LEDs según el valor leído de los interruptores.
3. Cada caso de la declaración `switch` asigna un valor binario específico a los LEDs.
4. Después de cada asignación, el programa espera 0.25 segundos antes de volver a leer el valor de los interruptores.

### Casos de la Declaración `switch`

- `case 0`, `1`, `2`, `3`: Enciende el LED más a la derecha (`0b001`).
- `case 4`, `5`: Enciende el LED del medio (`0b010`).
- `case 6`, `7`: Enciende los dos LEDs más a la derecha (`0b011`).
- `case 8`, `9`, `10`, `11`: Enciende los dos LEDs más a la izquierda (`0b110`).
- `case 12`, `13`, `14`: Enciende el LED más a la izquierda (`0b100`).
- `case 15`: Enciende todos los LEDs (`0b111`).
- `default`: Apaga todos los LEDs (`0b000`).

### Espera

El programa utiliza `wait(0.25)` para introducir un retraso de 0.25 segundos entre cada lectura de los interruptores, lo que permite una operación más suave y evita cambios rápidos en los LEDs.

## Requisitos

- Plataforma Mbed
- Microcontrolador compatible con Mbed
- Conexión de hardware adecuada para los interruptores y los LEDs

## Uso

Para utilizar este programa, asegúrese de tener configurada la plataforma Mbed y conecte los interruptores y los LEDs a los pines especificados en el código. Compile y cargue el programa en su microcontrolador y observe cómo los LEDs cambian de estado según el valor de los interruptores.