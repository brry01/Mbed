# Mbed

## Descripción

Este repositorio contiene una colección de proyectos y ejemplos desarrollados para Mbed OS. Cada proyecto se encuentra en su propio directorio y está diseñado para ilustrar diferentes funciones y características de Mbed OS.

## Contenido del Repositorio

1. [Barberia](./barberia)
2. [Botón Programación Asíncrona](./boton_programacion_asincrona)
3. [Botones LED](./botones_led)
4. [Buses](./buses)
5. [Control por Bits](./control_por_bits)
6. [Control por Buses](./control_por_buses)
7. [Display](./display)
8. [Display Shift Register](./display_shift_register)
9. [Interrupciones](./interrupciones)
10. [Motor](./motor)
11. [Sistema de Seguridad para Máquina](./sistema_de_seguridad_para_maquina)

### Barberia

Este código implementa una simulación de un sistema de barbería utilizando el framework Mbed, donde se emplean interrupciones y temporizadores para gestionar el flujo de clientes (adultos y niños) y manejar situaciones de emergencia. El sistema utiliza pines de hardware para representar botones y LEDs, y modela la disponibilidad de barberos y asientos en la barbería.

### Botón Programación Asíncrona

Este proyecto demuestra cómo usar una interrupción para controlar un LED en una placa Mbed. El programa configura un botón para que dispare una interrupción cuando se presiona, lo que alterna el estado de un LED.


### Botones LED

Este proyecto en Mbed permite controlar tres LEDs utilizando cuatro botones. Cada botón realiza una acción diferente sobre los LEDs.

### Buses

Este archivo contiene un programa en C++ que utiliza la plataforma Mbed para leer el estado de un conjunto de interruptores y controlar un conjunto de LEDs en función del valor leído.

### Control por Bits

Este proyecto utiliza la plataforma Mbed para controlar tres LEDs (rojo, amarillo y azul) mediante el estado de cuatro interruptores. El comportamiento de los LEDs depende de la combinación de los estados de los interruptores.

### Control por Buses

Este programa implementa un sistema de control por buses utilizando el framework Mbed. Dependiendo del valor de entrada en un bus de interruptores (`BusIn`), se encienden diferentes combinaciones de LEDs (`BusOut`). El programa utiliza una estructura `switch` para determinar qué LEDs deben encenderse según el valor del bus de entrada.

### Display

Este proyecto contiene un código para controlar un display de 7 segmentos utilizando la plataforma Mbed.

### Display Shift Register

1. **Control de LCD con registro de desplazamiento y Mbed**  
   Programa que inicializa y gestiona un LCD mediante un registro de desplazamiento y comunicación SPI en la plataforma Mbed. Permite limpiar la pantalla y mostrar texto.

2. **Control de LCD y sensor de temperatura MAX6675 con Mbed**  
   Programa que gestiona un LCD y un sensor de temperatura MAX6675 utilizando un registro de desplazamiento 74HC595 y la plataforma Mbed. Muestra mensajes en el LCD y actualiza periódicamente la temperatura medida.

3. **Control de LCD, sensor de temperatura, potenciómetro y LED con Mbed**  
   Programa que gestiona un LCD, un sensor de temperatura MAX6675, un potenciómetro y un LED con PWM mediante un registro de desplazamiento 74HC595 en la plataforma Mbed. Permite visualizar mensajes en el LCD, medir la temperatura, ajustar la intensidad del LED según el potenciómetro y actualizar los datos periódicamente.

### Interrupciones

Este proyecto demuestra el uso de interrupciones en Mbed OS utilizando la clase `InterruptIn`. El archivo `interrupciones.txt` contiene un ejemplo de cómo configurar y utilizar interrupciones en Mbed OS. El programa define una clase `Counter` que incrementa un contador cada vez que se detecta una interrupción en el pin especificado.

### Motor

Este archivo contiene el código para controlar un motor utilizando la biblioteca Mbed. A continuación se describe la funcionalidad del código y los pines utilizados. El código controla el estado de un motor basado en las entradas de varios pines digitales. Además, utiliza cuatro LEDs para indicar diferentes estados del sistema.


### Sistema de Seguridad para Máquina

Este proyecto implementa un sistema de seguridad para una máquina utilizando el microcontrolador Mbed. El sistema controla el arranque, operación y parada del motor de la máquina, asegurando que no haya condiciones peligrosas antes de permitir su funcionamiento.

## Instalación y Uso

```bash
git clone https://github.com/brry01/Mbed.git
cd Mbed
```

## Contacto

- **Nombre:** [Bernardo Paz]
- **Email:** [bernardo.pazsa@gmail.com]
- **GitHub:** [https://github.com/brry01](https://github.com/brry01)
