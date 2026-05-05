[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MCJunYEq)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23816917&assignment_repo_type=AssignmentRepo)
# Lab06: Comunicación UART con PIC18F45K22

## Integrantes

*[Steven Hinestroza Lopez]
(https://github.com/stevenh22)

*[Nicolas Andres Rodriguez Moreno]
(https://github.com/nicolasanrodriguezmo-dotcom)

## Documentación

La comunicación serial UART (Universal Asynchronous Receiver Transmitter) es un protocolo ampliamente utilizado en sistemas embebidos para la transmisión y recepción de datos entre dispositivos electrónicos. A diferencia de otros métodos de comunicación, UART opera de manera asíncrona, lo que significa que no requiere una señal de reloj compartida entre los dispositivos, simplificando su implementación y reduciendo el número de conexiones necesarias.

En los microcontroladores PIC, el módulo UART permite establecer comunicación con periféricos externos como computadoras, módulos Bluetooth, sensores y otros sistemas digitales. Para su correcto funcionamiento, es necesario configurar parámetros fundamentales como la velocidad de transmisión (baudrate), el modo de operación, la longitud de datos y la frecuencia del oscilador del sistema.

### Descripcion y funcionamiento del sistema

El sistema implementado se divide en dos componentes principales: el módulo de comunicación UART y el programa principal encargado de ejecutar la lógica del sistema.

Por un lado, el módulo UART se encarga de configurar los registros internos del microcontrolador necesarios para la comunicación serial. Esto incluye la definición del baudrate en 9600 bps, la selección del modo asíncrono y la habilitación de los módulos de transmisión y recepción. Además, se configuran los pines correspondientes, estableciendo el pin TX como salida y el pin RX como entrada. Dentro de este módulo se implementan funciones que permiten enviar datos, ya sea carácter por carácter o mediante cadenas de texto completas, lo cual simplifica la interacción con otros dispositivos.

Por otro lado, el programa principal inicializa el sistema configurando el oscilador interno del microcontrolador a una frecuencia de 16 MHz, lo cual es fundamental para garantizar la correcta sincronización en la comunicación UART. Posteriormente, se llama a la función de inicialización del UART y se ejecuta un ciclo infinito en el que se envía periódicamente un mensaje de texto a través del puerto serial.

El funcionamiento del sistema consiste en transmitir la cadena “Hola desde el PIC” seguida de caracteres de control que generan un salto de línea, permitiendo que los datos se visualicen de manera ordenada en un monitor serial. Este proceso se repite continuamente con un retardo de un segundo entre cada transmisión, lo que facilita la observación de los datos enviados.


## Diagramas

![alt text](Uart.gif)

El diagrama del sistema representa la conexión entre el microcontrolador PIC y un computador mediante comunicación serial UART. Para establecer la comunicación, se realiza una conexión cruzada entre los pines de transmisión y recepción, donde el pin TX (RC6) del microcontrolador se conecta al pin RX del convertidor USB-Serial, y el pin RX (RC7) se conecta al pin TX del mismo dispositivo. Adicionalmente, se establece una conexión a tierra común (GND) entre ambos sistemas para garantizar una referencia de voltaje adecuada.

El microcontrolador actúa como emisor de datos, enviando información a través del pin TX, la cual es recibida por el computador y visualizada en un monitor serial. Esta configuración permite la comunicación efectiva entre el sistema embebido y dispositivos externos, siendo ampliamente utilizada en aplicaciones de monitoreo y depuración.


## Evidencias de implementación

![alt text](Diagrama-que-se-actualiza-.gif)

El diagrama del sistema representa la comunicación entre un microcontrolador PIC y un computador mediante el protocolo UART, utilizando un convertidor USB a serial. El microcontrolador transmite datos a través del pin TX (RC6), los cuales son enviados al pin RX del módulo USB-TTL. Este dispositivo convierte la señal a un formato compatible con el computador, permitiendo que sea interpretada por un programa desarrollado en Python.

En el computador, se utiliza una librería de comunicación serial para leer los datos provenientes del puerto COM configurado a 9600 baudios, coincidiendo con la configuración del microcontrolador. Los datos recibidos son procesados y mostrados en tiempo real, lo que permite visualizar la información transmitida desde el sistema embebido.

Este tipo de arquitectura es común en aplicaciones de monitoreo, adquisición de datos y depuración, donde un microcontrolador envía información a un sistema de mayor capacidad de procesamiento para su análisis y visualización.