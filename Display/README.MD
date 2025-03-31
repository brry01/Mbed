# Display Control con Mbed

Este proyecto contiene un código para controlar un display de 7 segmentos utilizando la plataforma Mbed.

## Descripción

El código en `display.txt` configura un bus de salida (`BusOut`) con pines conectados a un display de 7 segmentos. El programa muestra una secuencia de números (0 a 3) en el display, actualizándose cada 0.2 segundos.

## Código

```cpp
#include "mbed.h"

BusOut display(p5, p6, p7, p8, p9, p10, p11, p12);
// Segments connected in sequence a, b, c, d, e, f, g, dp
int main() {
    while(1) {
        for(int i = 0; i < 4; i++) {
            switch (i) {
                case 0: display = 0x3F; break;
                case 1: display = 0x06; break;
                case 2: display = 0x5B; break;
                case 3: display = 0x4F; break;
            }
            wait(0.2);
        }
    }
}
```

## Conexiones

Los pines utilizados para el bus de salida (`BusOut`) son p5, p6, p7, p8, p9, p10, p11 y p12. Estos pines están conectados secuencialmente a los segmentos del display (a, b, c, d, e, f, g, dp).

## Funcionamiento

El código hace que el display muestre los números 0, 1, 2 y 3 en secuencia, con un retardo de 0.2 segundos entre cada número. Los valores hexadecimales asignados a `display` corresponden a las configuraciones de los segmentos para mostrar cada número:

- `0x3F`: Muestra el número 0.
- `0x06`: Muestra el número 1.
- `0x5B`: Muestra el número 2.
- `0x4F`: Muestra el número 3.

## Requisitos

- Plataforma Mbed
- Display de 7 segmentos
- Conexión adecuada de los pines a los segmentos del display

## Compilación y Ejecución

1. Clona este repositorio.
2. Compila el código utilizando el compilador de Mbed.
3. Carga el binario resultante en tu dispositivo Mbed.
4. Conecta los pines adecuados al display de 7 segmentos.
5. Ejecuta el programa y observa la secuencia de números en el display.