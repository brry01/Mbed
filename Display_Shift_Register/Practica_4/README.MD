# Display Shift Register - Práctica 4

Este programa implementa el control de un LCD utilizando un registro de desplazamiento y la plataforma Mbed. El código está diseñado para inicializar, limpiar y mostrar texto en un LCD mediante comunicación SPI.

## Descripción del Código

El programa utiliza las siguientes funcionalidades principales:

1. **Inicialización del LCD**: Configura el LCD para su funcionamiento.
2. **Limpieza del LCD**: Borra el contenido de la pantalla.
3. **Impresión de Texto**: Permite mostrar cadenas de texto en el LCD.
4. **Comunicación SPI**: Utiliza un registro de desplazamiento para enviar datos al LCD.

### Funciones Principales

- `init_lcd()`: Inicializa el LCD con los comandos necesarios.
- `clr_lcd()`: Limpia la pantalla del LCD.
- `print_lcd(const char *string)`: Muestra una cadena de texto en el LCD.
- `shift_out(int data)`: Envía datos al registro de desplazamiento mediante SPI.
- `write_cmd(int cmd)`: Envía un comando al LCD.
- `write_data(char c)`: Envía un carácter al LCD.
- `write_4bit(int data, int mode)`: Envía datos en modo de 4 bits al LCD.

### Pines Utilizados

- **D10**: Pin de selección de chip (CS) para la comunicación SPI.
- **D11**: MOSI (Master Out Slave In) para enviar datos al registro de desplazamiento.
- **D12**: MISO (Master In Slave Out) no utilizado en este caso.
- **D13**: SCK (Serial Clock) para la sincronización de datos.

### Flujo del Programa

1. Se inicializa el LCD con `init_lcd()`.
2. Se limpia la pantalla con `clr_lcd()`.
3. Se muestra el texto "Hello world!" en la primera línea del LCD.
4. Se mueve el cursor a la segunda línea y se muestra el texto "Testing".
5. El programa entra en un bucle infinito para mantener el LCD activo.

## Requisitos

- **Hardware**: 
  - Microcontrolador compatible con Mbed.
  - LCD con interfaz de registro de desplazamiento.
  - Conexión SPI configurada correctamente.
- **Software**: 
  - Entorno de desarrollo Mbed.

## Compilación y Ejecución

1. Copia el archivo `display_shift_register_4.2.txt` en tu proyecto Mbed.
2. Configura los pines de acuerdo con tu hardware.
3. Compila y carga el programa en tu microcontrolador.
4. Observa el texto mostrado en el LCD.

## Notas

- Asegúrate de que el LCD esté correctamente conectado y alimentado.
- Los tiempos de espera (`wait_us`) son críticos para el correcto funcionamiento del LCD.

## Autor

Este programa fue desarrollado como parte de la práctica 4 de la materia Electrónica Digital Avanzada.

## Imágen de Práctica

![Image](https://github.com/user-attachments/assets/4bb4480b-a165-473c-8be6-ae95e175e60d)