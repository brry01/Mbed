# Simulación de Sistema de Barbería con Mbed

Este código implementa una simulación de un sistema de barbería utilizando el framework Mbed, donde se emplean interrupciones y temporizadores para gestionar el flujo de clientes (adultos y niños) y manejar situaciones de emergencia. El sistema utiliza pines de hardware para representar botones y LEDs, y modela la disponibilidad de barberos y asientos en la barbería.

## Componentes Principales

- **InterruptIn**: Los objetos `boton_adulto`, `boton_nino` y `boton_incendio` están configurados para manejar las pulsaciones de botones de adultos, niños y emergencias, respectivamente.
- **BusOut**: El objeto `asientos` representa el estado de los 8 asientos en la barbería, donde cada bit corresponde a la disponibilidad de un asiento.
- **Variables de Estado**:
  - `asientos_disponibles`: Número de asientos disponibles.
  - `adultos_esperando`: Número de adultos esperando.
  - `ninos_esperando`: Número de niños esperando.
  - `emergencia`: Bandera booleana que indica si hay una emergencia activa.

## Funciones Principales

### `actualizar_leds`
Actualiza la representación de los LEDs según la disponibilidad de los asientos.

### `adulto_interrupcion` y `nino_interrupcion`
Se activan cuando un adulto o un niño presiona su respectivo botón. Estas funciones:
1. Verifican si no hay una emergencia activa.
2. Comprueban si hay suficientes asientos disponibles.
3. Decrementan el conteo de asientos.
4. Incrementan el conteo de espera.
5. Actualizan los LEDs.

### `incendio_interrupcion`
Maneja las situaciones de emergencia:
- Reinicia el estado del sistema.
- Detiene todos los temporizadores.
- Apaga los LEDs de los asientos.

## Función `main`

La función `main` configura los manejadores de interrupciones y entra en un bucle infinito para gestionar las operaciones de los barberos. 

### Operaciones de los Barberos
- Cada barbero está representado por un objeto `Timer` (`barbero1`, `barbero2` y `barbero3`).
- **Barberos 1 y 2**: Atienden a adultos.
- **Barbero 3**: Atiende a niños.

### Lógica del Bucle
1. Verifica si hay clientes esperando.
2. Comprueba si el temporizador de un barbero ha alcanzado los 12 segundos (indicando que se completó un corte de cabello).
   - Si es así:
     - Reinicia el temporizador del barbero.
     - Actualiza el conteo de asientos.
     - Decrementa el conteo de espera.
3. Si un barbero está inactivo (valor del temporizador es 0) y hay clientes esperando, inicia el temporizador del barbero.
4. Incluye un retraso de 100 ms para evitar un uso excesivo de la CPU.

## Resumen

Este sistema modela de manera efectiva una barbería con restricciones en tiempo real, utilizando interrupciones para la entrada de usuarios y temporizadores para la programación de tareas. También incluye un mecanismo robusto para manejar emergencias reiniciando el estado del sistema.

## Imágenes de Práctica
**Inicio**
![Image](https://github.com/user-attachments/assets/413bf66e-1237-4b02-97b0-cf78817a909b)

**Adulto**
![Image](https://github.com/user-attachments/assets/11b97f77-bb94-4316-9b4e-41370478c43f)

**Niño**
![Image](https://github.com/user-attachments/assets/1e8b7e07-87e0-45a5-ac67-a9e4c9fd3e75)

**Adulto y Niño**
![Image](https://github.com/user-attachments/assets/e9c1e940-66b4-4975-8002-ba16de0d43fd)

**Dos Niños**
![Image](https://github.com/user-attachments/assets/04580b57-9c74-4b65-bb9b-3d8a7f3f1cd7)

**Asientos Ocupados**
![Image](https://github.com/user-attachments/assets/237ad157-7c43-4db2-974a-11b7a44d3c95)

**Emergencia**
![Image](https://github.com/user-attachments/assets/ccbee47d-552b-4448-ac3d-bc6e046be732)
