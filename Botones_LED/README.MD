```markdown
# Botones y LEDs con Mbed

Este proyecto en Mbed permite controlar tres LEDs utilizando cuatro botones. Cada botón realiza una acción diferente sobre los LEDs.

## Hardware Requerido

- Placa Mbed compatible
- 3 LEDs (uno rojo, uno amarillo y uno azul)
- 4 botones
- Conexiones GPIO de la placa Mbed

## Conexiones

- Botón 1 conectado a `p5`
- Botón 2 conectado a `p6`
- Botón 3 conectado a `p7`
- Botón 4 conectado a `p8`
- LED rojo conectado a `p9`
- LED amarillo conectado a `p10`
- LED azul conectado a `p11`

## Código

El código define las conexiones y las funciones de interrupción para los botones, y controla los LEDs basándose en las interrupciones.

### Definición de Pines

```cpp
#define BUTTON_1 p5
#define BUTTON_2 p6
#define BUTTON_3 p7
#define BUTTON_4 p8

#define RED_LED p9
#define YELLOW_LED p10
#define BLUE_LED p11
```

### Configuración de Salidas e Interrupciones

```cpp
DigitalOut led1(RED_LED);
DigitalOut led2(YELLOW_LED);
DigitalOut led3(BLUE_LED);

InterruptIn button_1(BUTTON_1);
InterruptIn button_2(BUTTON_2);
InterruptIn button_3(BUTTON_3);
InterruptIn button_4(BUTTON_4);
```

### Funciones Callback

```cpp
void button_1_handler(){
    // Toggle LED 1
    led1 = !led1;
}

void button_2_handler(){
    // Toggle LED 2
    led2 = !led2;
}

void button_3_handler(){
    // Toggle LED 3
    led3 = !led3;
}

void button_4_handler(){
    // Encender todos los LEDs
    led1 = 1;
    led2 = 1;
    led3 = 1;
}
```

### Función Principal

```cpp
int main(){
    // Apagar LEDs al inicio
    led1 = 0;
    led2 = 0;
    led3 = 0;

    // Asignar handlers a las interrupciones
    button_1.rise(&button_1_handler);
    button_2.rise(&button_2_handler);
    button_3.rise(&button_3_handler);
    button_4.rise(&button_4_handler);

    // Bucle principal
    while(1){
        wait_ms(100);
    }
}
```

## Funcionamiento

- El **Botón 1** alterna el estado del LED rojo.
- El **Botón 2** alterna el estado del LED amarillo.
- El **Botón 3** alterna el estado del LED azul.
- El **Botón 4** enciende todos los LEDs.

Este código es un ejemplo básico de cómo usar interrupciones con botones para controlar LEDs en una placa Mbed.
```