# Interrupciones en Mbed

Este proyecto demuestra el uso de interrupciones en Mbed OS utilizando la clase `InterruptIn`.

## Descripción

El archivo `interrupciones.txt` contiene un ejemplo de cómo configurar y utilizar interrupciones en Mbed OS. El programa define una clase `Counter` que incrementa un contador cada vez que se detecta una interrupción en el pin especificado.

## Código

```cpp
#include "mbed.h"

class Counter{
    public:
        // Crear InterruptIn en el pin especifico al counter
        Counter(PinName pin): _interrupt(pin){
            // Adiere la función increment al counter de esta instancia
            _interrupt.rise(callback(this,&Counter::increment));
        }
        
        void increment(){
            _count++;
        }
        
        int read(){
            return _count;
        }
        
    private:
        InterruptIn _interrupt;
        volatile int _count;
};

Counter counter(SW2);

int main(){
    while(1){
        printf("%d", counter.read());
    }
}
```

## Explicación del Código

- **Clase Counter**: Esta clase contiene un constructor que configura una interrupción en el pin especificado y liga la función `increment` para que se ejecute cuando la interrupción se active. También contiene un método `read` para leer el valor del contador.
- **InterruptIn**: Utiliza la clase `InterruptIn` que permite configurar interrupciones en pines específicos.
- **Método increment**: Incrementa el contador cada vez que se detecta una interrupción.
- **Método read**: Devuelve el valor actual del contador.
- **Función principal**: En la función `main`, se crea una instancia de `Counter` y se imprime el valor del contador en un bucle infinito.

## Uso

Para utilizar este ejemplo, simplemente compile y cargue el programa en su dispositivo Mbed compatible. Cada vez que se detecte una interrupción en el pin configurado (en este caso `SW2`), el contador se incrementará.