# Sistema de Seguridad para Máquina

Este proyecto implementa un sistema de seguridad para una máquina utilizando el microcontrolador Mbed. El sistema controla el arranque, operación y parada del motor de la máquina, asegurando que no haya condiciones peligrosas antes de permitir su funcionamiento.

## Descripción

El programa utiliza varias entradas digitales para monitorear el estado de botones y sensores, y salidas digitales para controlar LEDs indicadores. A continuación, se describen los elementos principales del sistema:

### Entradas

- **BotonArranque (p5):** Botón para arrancar el motor.
- **BotonParo (p6):** Botón para detener el motor.
- **Guarda (p7):** Sensor de la guarda de seguridad.
- **Temperatura (p8):** Sensor de temperatura.

### Salidas

- **led1 (p9):** Indica que el motor está listo para arrancar.
- **led2 (p10):** Indica que el motor está en funcionamiento.
- **led3 (p11):** Indica una falla en la guarda de seguridad.
- **led4 (p12):** Indica un exceso de temperatura.

## Estados del Motor

- **MotorCorriendo:** Indica si el motor está en funcionamiento.
- **MotorListo:** Indica si el motor está listo para arrancar.

## Funciones

- **VerificacionMotor():** Verifica si el motor está listo para arrancar basándose en el estado de la guarda de seguridad y la temperatura.
- **main():** Bucle principal que controla el arranque, operación y parada del motor, y maneja las condiciones de falla.

### Ejemplo de Código

```cpp
#include "mbed.h"

DigitalIn BotonArranque(p5);  
DigitalIn BotonParo(p6);      
DigitalIn Guarda(p7);         
DigitalIn Temperatura(p8);   

DigitalOut led1(p9);   // Motor listo para arrancar
DigitalOut led2(p10);  // Motor está trabajando
DigitalOut led3(p11);  // Falla de guarda de seguridad
DigitalOut led4(p12);  // Exceso de temperatura

bool MotorCorriendo = false;  
bool MotorListo = false;     

void VerificacionMotor() {
    if(Guarda.read() == 1 && Temperatura.read() == 0) {
        MotorListo = true;
        led1 = 1;  
    } else {
        MotorListo = false;
        led1 = 0; 
    }
}

int main() {
    while (1) {
        VerificacionMotor();

        if(MotorListo && BotonArranque.read() == 1 && !MotorCorriendo){
            MotorCorriendo = true;
            led2 = 1;  
            led3 = 0;  
            led4 = 0;  
        }

        if(MotorCorriendo){
            if (Guarda.read() == 0) {
                MotorCorriendo = false;
                led3 = 1;  
                led2 = 0;  
            } else if (Temperatura.read() == 1) {
                MotorCorriendo = false;
                led4 = 1;  
                led2 = 0;  
            }
        }

        if (BotonParo.read() == 1 && MotorCorriendo) {
            MotorCorriendo = false;
            led2 = 0;  
        }

        if (!MotorCorriendo) {
            if (BotonParo.read() == 0) {  
                if (MotorListo) {  
                    led1 = 1;  
                }
            }
        }

        if (!MotorListo) {
            led1 = !led1; 
            wait(0.5);  
        }
        
        wait(0.1);  
    }
}
```

## Cómo Usar

1. **Conectar los componentes:**
   - Conecte los botones a los pines p5 y p6.
   - Conecte los sensores de guarda y temperatura a los pines p7 y p8.
   - Conecte los LEDs a los pines p9, p10, p11 y p12.

2. **Cargar el programa en el microcontrolador Mbed.**

3. **Operar la máquina:**
   - Presione el botón de arranque para iniciar el motor si las condiciones son seguras.
   - Presione el botón de paro para detener el motor en cualquier momento.
   - Observe los LEDs para el estado del sistema y las condiciones de falla.

## Notas

- Asegúrese de que la guarda de seguridad esté cerrada y la temperatura esté dentro de los límites seguros antes de arrancar el motor.
- El sistema parpadea el LED de motor listo cuando no está en condiciones de arrancar.