# Display Shift Register - Práctica 5

Este programa controla un LCD y un sensor de temperatura MAX6675 utilizando un registro de desplazamiento 74HC595 y la plataforma Mbed. El código permite mostrar mensajes en el LCD y leer la temperatura del sensor, actualizándola periódicamente.

## Descripción del Código

El programa utiliza las siguientes funcionalidades principales:

1. **Control del LCD**: Manejo del LCD mediante un registro de desplazamiento 74HC595.
2. **Lectura de Temperatura**: Comunicación con el sensor MAX6675 para obtener la temperatura en grados Celsius.
3. **Interfaz SPI**: Comunicación serial para controlar tanto el 74HC595 como el MAX6675.

### Funciones Principales

#### Control del LCD
- `lcdInit()`: Inicializa el LCD en modo de 4 bits.
- `lcdCommand(uint8_t cmd)`: Envía un comando al LCD.
- `lcdData(char data)`: Envía un carácter al LCD.
- `lcdPrint(const char* str)`: Muestra una cadena de texto en el LCD.

#### Comunicación SPI
- `shiftOut(uint8_t data)`: Envía datos al registro de desplazamiento 74HC595.
- `pulseEnable(uint8_t data)`: Genera un pulso de habilitación para el LCD.
- `sendNibble(uint8_t nibble, bool rs)`: Envía un nibble (4 bits) al LCD.
- `sendByte(uint8_t value, bool rs)`: Envía un byte completo al LCD.

#### Lectura del MAX6675
- `readTemperature()`: Lee la temperatura del sensor MAX6675 y la convierte a grados Celsius.

### Flujo del Programa

1. Configura la interfaz SPI y el LCD.
2. Muestra el mensaje "Iniciando..." en el LCD.
3. En un bucle infinito:
   - Lee la temperatura del sensor MAX6675.
   - Muestra la temperatura en el puerto serial.
   - Actualiza la temperatura en el LCD.

### Pines Utilizados

- **D11**: MOSI (Master Out Slave In) para enviar datos al 74HC595 y MAX6675.
- **D12**: MISO (Master In Slave Out) para recibir datos del MAX6675.
- **D13**: SCK (Serial Clock) para la sincronización de datos.
- **D10**: Latch del 74HC595.
- **D9**: Chip Select (CS) del MAX6675.

## Requisitos

- **Hardware**:
  - Microcontrolador compatible con Mbed.
  - Registro de desplazamiento 74HC595.
  - Sensor de temperatura MAX6675.
  - LCD con interfaz de 4 bits.
- **Software**:
  - Entorno de desarrollo Mbed.

## Compilación y Ejecución

1. Copia el archivo `display_shift_register_5.1.txt` en tu proyecto Mbed.
2. Configura los pines de acuerdo con tu hardware.
3. Compila y carga el programa en tu microcontrolador.
4. Observa la temperatura en el LCD y en el puerto serial.

## Notas

- Asegúrate de que el sensor MAX6675 esté correctamente conectado y alimentado.
- Los tiempos de espera (`ThisThread::sleep_for`) son críticos para el correcto funcionamiento del LCD y el sensor.
- Si el sensor MAX6675 no está conectado o presenta un error, la función `readTemperature()` devolverá `-1`.

## Autor

Este programa fue desarrollado como parte de la práctica 5 de la materia Electrónica Digital Avanzada.

## Imágenes de Práctica
**Punto 1**
![Image](https://github.com/user-attachments/assets/49ee7fd5-be45-4265-9edd-854f5b96a714)

** Punto 2**
![Image](https://github.com/user-attachments/assets/12f89d10-c882-4b52-b5f5-15f2b890733f)

**Punto 3**
![Image](https://github.com/user-attachments/assets/b1da78ff-f1cb-4699-be59-3c49fa3ca495)