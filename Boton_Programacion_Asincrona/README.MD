# Botón de Programación Asíncrona

Este proyecto demuestra cómo usar una interrupción para controlar un LED en una placa Mbed.

## Descripción

El programa configura un botón para que dispare una interrupción cuando se presiona, lo que alterna el estado de un LED.

## Código

```cpp
#include "mbed.h"

InterruptIn button_press(p12);
DigitalOut Led_out(p13);

void button_ISR() {
    Led_out = !Led_out;
}

int main() {
    button_press.rise(&button_ISR); // Rise = De 0 a 1 lógico.
    while(1) {
    }
}

// Fall = De 1 a 0 lógico.
```

## Explicación

- `InterruptIn button_press(p12);`: Configura el pin `p12` como una entrada de interrupción.
- `DigitalOut Led_out(p13);`: Configura el pin `p13` como una salida digital para controlar el LED.
- `void button_ISR()`: Función de servicio de interrupción que se llama cuando se presiona el botón. Esta función alterna el estado del LED.
- `button_press.rise(&button_ISR);`: Vincula la función de interrupción `button_ISR` para que se llame cuando el botón cambia de estado bajo (0 lógico) a alto (1 lógico).

## Notas

- La interrupción se configura para dispararse en el flanco de subida (cuando el botón cambia de 0 a 1 lógico).
- El bucle `while(1)` mantiene el programa en ejecución indefinidamente.