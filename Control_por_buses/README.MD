# Control por Buses con Mbed

Este programa implementa un sistema de control por buses utilizando el framework Mbed. Dependiendo del valor de entrada en un bus de interruptores (`BusIn`), se encienden diferentes combinaciones de LEDs (`BusOut`). El programa utiliza una estructura `switch` para determinar qué LEDs deben encenderse según el valor del bus de entrada.

## Descripción del Hardware

- **Entradas**:
  - `BusIn mySwitches(p5, p6, p7, p8)`: Un bus de 4 pines (p5, p6, p7, p8) que representa un conjunto de interruptores.
- **Salidas**:
  - `BusOut myleds(p9, p10, p11)`: Un bus de 3 pines (p9, p10, p11) que controla tres LEDs:
    - LED Rojo (p9)
    - LED Amarillo (p10)
    - LED Azul (p11)

## Lógica del Programa

El programa evalúa continuamente el valor del bus de entrada (`mySwitches`) en un bucle infinito. Según el valor leído, se encienden diferentes combinaciones de LEDs:

- **Valores 0 a 3**: Se enciende únicamente el LED Rojo (`0b100`).
- **Valores 4 y 5**: Se enciende únicamente el LED Amarillo (`0b010`).
- **Valores 6 y 7**: Se encienden los LEDs Rojo y Amarillo (`0b110`).
- **Valores 8 a 11**: Se encienden los LEDs Amarillo y Azul (`0b011`).
- **Valores 12 a 14**: Se enciende únicamente el LED Azul (`0b001`).
- **Valor 15**: Se encienden todos los LEDs (`0b111`).

## Flujo del Programa

1. **Inicialización**:
   - Se configuran los buses de entrada (`mySwitches`) y salida (`myleds`).
2. **Bucle Infinito**:
   - Se evalúa el valor del bus de entrada (`mySwitches`) utilizando una estructura `switch`.
   - Según el caso correspondiente, se asigna un valor binario al bus de salida (`myleds`) para encender los LEDs deseados.
3. **Control de LEDs**:
   - Los LEDs se encienden o apagan según el valor asignado al bus de salida.

## Ejemplo de Funcionamiento

| Valor de `mySwitches` | LEDs Encendidos | Valor Binario |
|------------------------|-----------------|---------------|
| 0, 1, 2, 3            | Rojo            | `0b100`       |
| 4, 5                  | Amarillo        | `0b010`       |
| 6, 7                  | Rojo y Amarillo | `0b110`       |
| 8, 9, 10, 11          | Amarillo y Azul | `0b011`       |
| 12, 13, 14            | Azul            | `0b001`       |
| 15                    | Todos           | `0b111`       |

## Requisitos

- **Hardware**:
  - Placa compatible con Mbed.
  - 4 interruptores conectados a los pines p5, p6, p7 y p8.
  - 3 LEDs conectados a los pines p9, p10 y p11.
- **Software**:
  - Framework Mbed.

## Notas

- Este programa utiliza buses para simplificar el control de múltiples pines de entrada y salida.
- Asegúrese de que los pines utilizados estén correctamente configurados en el hardware.

## Autor

Este programa fue desarrollado como parte de un proyecto de Electrónica Digital Avanzada.