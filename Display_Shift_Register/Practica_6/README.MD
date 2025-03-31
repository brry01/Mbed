# Display Shift Register - Práctica 6

Este programa controla un LCD, un sensor de temperatura MAX6675, un potenciómetro y un LED con PWM utilizando un registro de desplazamiento 74HC595 y la plataforma Mbed. El código permite mostrar mensajes en el LCD, leer la temperatura del sensor, ajustar la intensidad del LED según el potenciómetro y actualizar la información periódicamente.

## Descripción del Código

El programa utiliza las siguientes funcionalidades principales:

1. **Control del LCD**: Manejo del LCD mediante un registro de desplazamiento 74HC595.
2. **Lectura de Temperatura**: Comunicación con el sensor MAX6675 para obtener la temperatura en grados Celsius.
3. **Control de LED con PWM**: Ajuste de la intensidad del LED en función del valor leído del potenciómetro.
4. **Interfaz SPI**: Comunicación serial para controlar tanto el 74HC595 como el MAX6675.

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

#### Control del LED con PWM
- `led.write(float value)`: Ajusta la intensidad del LED en función del valor del potenciómetro (0.0 a 1.0).

### Flujo del Programa

1. Configura la interfaz SPI, el LCD y el LED con PWM.
2. Muestra el mensaje "Iniciando..." en el LCD.
3. En un bucle infinito:
   - Lee la temperatura del sensor MAX6675.
   - Lee el valor del potenciómetro.
   - Muestra la temperatura y el contador en el puerto serial.
   - Actualiza la temperatura y el contador en el LCD.
   - Ajusta la intensidad del LED según el valor del potenciómetro.

### Pines Utilizados

- **D11**: MOSI (Master Out Slave In) para enviar datos al 74HC595 y MAX6675.
- **D12**: MISO (Master In Slave Out) para recibir datos del MAX6675.
- **D13**: SCK (Serial Clock) para la sincronización de datos.
- **D10**: Latch del 74HC595.
- **D9**: Chip Select (CS) del MAX6675.
- **D3**: LED con PWM.
- **A0**: Entrada analógica para el potenciómetro.

## Requisitos

- **Hardware**:
  - Microcontrolador compatible con Mbed.
  - Registro de desplazamiento 74HC595.
  - Sensor de temperatura MAX6675.
  - LCD con interfaz de 4 bits.
  - Potenciómetro.
  - LED.
- **Software**:
  - Entorno de desarrollo Mbed.

## Compilación y Ejecución

1. Copia el archivo `display_shift_register_6.3.txt` en tu proyecto Mbed.
2. Configura los pines de acuerdo con tu hardware.
3. Compila y carga el programa en tu microcontrolador.
4. Observa la temperatura, el contador y el ajuste del LED en el LCD y en el puerto serial.

## Notas

- Asegúrate de que el sensor MAX6675 esté correctamente conectado y alimentado.
- Los tiempos de espera (`ThisThread::sleep_for`) son críticos para el correcto funcionamiento del LCD y el sensor.
- Si el sensor MAX6675 no está conectado o presenta un error, la función `readTemperature()` devolverá `-1`.
- El valor del potenciómetro debe estar en el rango de 0.0 a 1.0 para ajustar correctamente la intensidad del LED.

## Autor

Este programa fue desarrollado como parte de la práctica 6 de la materia Electrónica Digital Avanzada.
