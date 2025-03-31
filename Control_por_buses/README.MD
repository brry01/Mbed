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

## Imágenes de Práctica

![Image](https://github.com/user-attachments/assets/6a65474f-bb1c-48ca-84ee-fb8f6442246c)
![Image](https://github.com/user-attachments/assets/3b7451b1-d185-414c-85f8-57145cf46256)
![Image](https://github.com/user-attachments/assets/3a3185a0-4053-4e98-ad90-c0511842573a)
![Image](https://github.com/user-attachments/assets/2a88a11a-eae0-4988-946d-8b8b254b22a7)
![Image](https://github.com/user-attachments/assets/542f6cba-9628-48b0-a83d-30ecff876170)
![Image](https://github.com/user-attachments/assets/8607d748-1b42-4d99-8abb-2340e5f5c1f6)
![Image](https://github.com/user-attachments/assets/65d372d6-3d2d-47a4-82a1-dede0d81808c)
![Image](https://github.com/user-attachments/assets/37e243b4-9959-4193-bc83-57d62db5757c)
![Image](https://github.com/user-attachments/assets/96613038-e901-4712-b9af-d2a91fdad6a1)
![Image](https://github.com/user-attachments/assets/1ff6f2bc-86cb-4dfd-b39d-31f824ccdf2a)
![Image](https://github.com/user-attachments/assets/d13498f5-0d61-40e4-a087-97952fefdc7c)
![Image](https://github.com/user-attachments/assets/09999380-4970-4792-8cdd-8288027e1acc)
![Image](https://github.com/user-attachments/assets/b2bd6d4c-828d-441c-ab59-296cec3dbb21)
![Image](https://github.com/user-attachments/assets/d74186a7-72f7-4810-946b-cdc383eb3544)
![Image](https://github.com/user-attachments/assets/fe185e49-2e5b-4810-ac8e-c2c7ece48a6e)
![Image](https://github.com/user-attachments/assets/a19bc992-0601-49f2-b302-805f915f0233)
![Image](https://github.com/user-attachments/assets/0be28edf-aff1-4764-8f80-06f3a0c2c3d6)
