# 2do-Parcial-
Segundo parcial del curso de Microprocesadores y Microcontroladores de la UMG

Para realizar esta entrega correspondiente al segundo parcila del curso de Microprocesadores y Microcontroladores se hizo uso de dos librerías, la stdint.h que es la librería estandar y la stm32l0xx.h dada por el fabricante, en este caso STM. Como primer punto tenemos la declaración de variables con valor cero para posteriormente cambiar su valor segun los datos que se ingresen por medio del keypad. Tambien las llamdas de funciones para el keypad y y configuraciones de filas. Se declara los valores correspondientes para desplegar cada dígito sen los displays. Se definien los puertos que se utilizaran para habilitar cada display. Se habilita el reloj de los GPIOS que se usarán. Para la comunicación serial se habilita el USART.

La lógica de la calculadora fue que primero se ingresa el primer valor de la operación que se va a realizar, valor que esta en la varible valor1, luego a presionar la tecla numeral el valor del primer valor se guarda en la variable val. Luego entra al siguietne if esperando que se ingrese el segundo valor digitandolo en el keypad. Luego se debe indicar en el keypad la operación que se desea realizar siendo A una suma, B una resta y C una multiplicación. Al finalizar se puede presionar de nuevo el numeral para que borre todos los valores y regresa al estado inicial esperando que se ingrese el primer valor para empezar una nueva operación. 


Adjunto link de youtube mostrando el funcionamiento de la calculadora y explicación del funcionamiento del código. 
https://youtu.be/sWrV1EO2ZG0

