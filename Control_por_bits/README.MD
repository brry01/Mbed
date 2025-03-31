# Control Por Bits

Este proyecto utiliza la plataforma Mbed para controlar tres LEDs (rojo, amarillo y azul) mediante el estado de cuatro interruptores. El comportamiento de los LEDs depende de la combinación de los estados de los interruptores.

## Descripción del Código

El archivo `control_bits.txt` incluye el siguiente código:

```cpp
#include "mbed.h"

DigitalIn switch0(p5);
DigitalIn switch1(p6);
DigitalIn switch2(p7);
DigitalIn switch3(p8);

DigitalOut ledRojo(p9);      
DigitalOut ledAmarillo(p10);
DigitalOut ledAzul(p11);    

int main() {
    while (1) {
        // Leer el estado de los switches
        int switchState = (switch0.read() << 0) | (switch1.read() << 1) | (switch2.read() << 2) | (switch3.read() << 3);

        if (switchState >= 0 && switchState <= 3) {
            ledRojo = 1; 
            ledAmarillo = 0;
            ledAzul = 0;

        } else if (switchState >= 4 && switchState <= 5) {
            ledRojo = 0;
            ledAmarillo = 1; 
            ledAzul = 0;

        } else if (switchState >= 6 && switchState <= 7) {
            ledRojo = 1; 
            ledAmarillo = 1; 
            ledAzul = 0;

        } else if (switchState >= 8 && switchState <= 11) {
            ledRojo = 0;
            ledAmarillo = 1; 
            ledAzul = 1; 
        } else if (switchState >= 12 && switchState <= 14) {
            ledRojo = 0;
            ledAmarillo = 0; 
            ledAzul = 1; 
        } else if (switchState == 15) {
            ledRojo = 1; 
            ledAmarillo = 1; 
            ledAzul = 1; 
        }
    }
}
```

## Funcionalidad

El código principal se ejecuta en un bucle infinito que realiza las siguientes acciones:

1. Lee el estado de los cuatro interruptores y combina estos estados en una variable `switchState`.
2. Dependiendo del valor de `switchState`, el código controla los LEDs de la siguiente manera:
    - Para valores de `switchState` entre 0 y 3, solo se enciende el LED rojo.
    - Para valores entre 4 y 5, solo se enciende el LED amarillo.
    - Para valores entre 6 y 7, se encienden el LED rojo y el LED amarillo.
    - Para valores entre 8 y 11, se encienden el LED amarillo y el LED azul.
    - Para valores entre 12 y 14, solo se enciende el LED azul.
    - Para el valor 15, se encienden todos los LEDs.

## Configuración de Hardware

- Los interruptores están conectados a los pines p5, p6, p7 y p8.
- Los LEDs están conectados a los pines p9, p10 y p11.

## Uso

Compila y carga este código en una placa compatible con Mbed. Conecta los interruptores y los LEDs a los pines especificados y observa el comportamiento de los LEDs según el estado de los interruptores.

file:///C:/Users/Usuario/Documents/School/4to%20Semestre/Electr%C3%B3nica%20Digital%20Avanzada/Programas/Mbed/Control_por_bits/Imagenes_Practica/WhatsApp%20Image%202025-03-27%20at%2018.55.17_88a0ddf8.jpg
