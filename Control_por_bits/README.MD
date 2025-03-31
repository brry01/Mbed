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

## Imágenes de Práctica

![Image](https://github.com/user-attachments/assets/6a277239-d74b-4d8b-8180-c95385155a96)
![Image](https://github.com/user-attachments/assets/91adf848-8b39-4fc8-8c0d-aa65777b3318)
![Image](https://github.com/user-attachments/assets/bbafd322-3fb6-436a-8a82-5765c5a4811b)
![Image](https://github.com/user-attachments/assets/4bb95823-b973-49af-aba4-fc15371983b4)
![Image](https://github.com/user-attachments/assets/3b9e202d-6a38-4120-b1ff-df8c45e695b7)
![Image](https://github.com/user-attachments/assets/1d13682a-e3a4-4787-9ae6-12982a8eb918)
![Image](https://github.com/user-attachments/assets/bcc94a93-f8d4-4f8c-8cc2-4689c2cc13d7)
![Image](https://github.com/user-attachments/assets/e71e3f32-763c-4946-af11-1a3b536e74a7)
![Image](https://github.com/user-attachments/assets/9d90af68-c914-4e20-92ed-50dbfe87968a)
![Image](https://github.com/user-attachments/assets/001ffdcf-4e5b-4ad6-b181-3adb099ef6d8)
![Image](https://github.com/user-attachments/assets/8ad75222-51c1-4db0-9051-be3136b2f482)
![Image](https://github.com/user-attachments/assets/11d8a04c-4435-440c-96b0-7995cf03d1f8)
![Image](https://github.com/user-attachments/assets/7f027f6e-557b-45da-9abb-7d175190b282)
![Image](https://github.com/user-attachments/assets/9cdb9b88-bd1a-44b9-b801-ea58624fd257)
![Image](https://github.com/user-attachments/assets/03a42090-dbff-43db-bbd5-5b910a12ba76)
