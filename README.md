# 2do-Parcial-
Segundo parcial del curso de Microprocesadores y Microcontroladores de la UMG

Para realizar esta entrega correspondiente al segundo parcila del curso de Microprocesadores y Microcontroladores se hizo uso de dos librerías, la stdint.h que es la librería estandar y la stm32l0xx.h dada por el fabricante, en este caso STM.
#include <stdint.h>
#include "stm32l053xx.h"


Como primer punto tenemos la declaración de variables con valor cero para posteriormente cambiar su valor segun los datos que se ingresen por medio del keypad. 
uint8_t valor1 = 0; 					//VARIABLE PARA GUARDAR EL PRIMER VALOR INGRESADO
uint8_t valor2 = 0; 					//VARIABLE PARA GUARDAR EL SEGUNDO VALOR INGRESADO
uint8_t operacion = 0;				 	//VALOR DEL SEGUNDO VALOR NOMBRADO
uint8_t operacion1 = 0; 				//

uint8_t estado = ESPERA_PRIMER_VALOR; 			//ESTADO INICIAL DE LA CALCULADORA
uint8_t val = 0;						//INICIALIZACION DE LA VARIABLE CON VALOR 0


Tambien las llamdas de funciones para el keypad y y configuraciones de filas
keyboard_config();						//LLAMA LA FUNCION DE CONFIGURACION DE LAS FILAS
key_pressed(); 							//LLAMA LA FUNCION DE MUX DE COLUMNAS PARA MOSTRAR EN DISPLAYS
calculador();


Se declara los valores correspondientes para desplegar cada dígito sen los displays.
if(val==0x00){ 								//DESPLIEGA NUMERO 0 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C
GPIOB->ODR |=0x01<<4; //SEGMENTO D
GPIOB->ODR |=0x01<<6; //SEGMENTO E
GPIOB->ODR |=0x01<<7; //SEGMENTO F

}else if(val==0x01){ 						//DESPLIEGAL NUMERO 1 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C

}else if(val==0x02){ 						//DESPLIEGA NUMERO 2 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<9; //SEGMENTO G
GPIOB->ODR |=0x01<<6; //SEGMENTO E
GPIOB->ODR |=0x01<<4; //SEGMENTO D

}else if(val==0x03){ 						//DESPLIEGA NUMERO3 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<9; //SEGMENTO G
GPIOB->ODR |=0x01<<3; //SEGMENTO C
GPIOB->ODR |=0x01<<4; //SEGMENTO D

}else if(val==0x04){ 						//DESPLIEGA NUMERO 4 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<7; //SEGMENTO F
GPIOB->ODR |=0x01<<9; //SEGMENTO G
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C

}else if(val==0x05){ 						//DESPLIEGA NUMERO 5 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<7; //SEGMENTO F
GPIOB->ODR |=0x01<<9; //SEGMENTO G
GPIOB->ODR |=0x01<<3; //SEGMENTO C
GPIOB->ODR |=0x01<<4; //SEGMENTO D

}else if(val==0x06){ 						//DESPLIEGA NUMERO 6 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<7; //SEGMENTO F
GPIOB->ODR |=0x01<<6; //SEGMENTO E
GPIOB->ODR |=0x01<<4; //SEGMENTO D
GPIOB->ODR |=0x01<<3; //SEGMENTO C
GPIOB->ODR |=0x01<<9; //SEGMENTO G

}else if(val==0x07){ 						//DESPLIEGA NUMERO 7 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C

}else if(val==0x08){ 						//DESPLIEGA NUMERO 8 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETEA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C
GPIOB->ODR |=0x01<<4; //SEGMENTO D
GPIOB->ODR |=0x01<<6; //SEGMENTO E
GPIOB->ODR |=0x01<<7; //SEGMENTO F
GPIOB->ODR |=0x01<<9; //SEGMENTO G

}else if(val==0x09){ 						//DESPLIEGA NUMERO 9 EN DISPLAY
GPIOB->BSRR=(0x3DC<<16); 					//RESETA TODOS LOS BITS A 0
GPIOB->ODR |=0x01<<9; //SEGMENTO G
GPIOB->ODR |=0x01<<7; //SEGMENTO F
GPIOB->ODR |=0x01<<8; //SEGMENTO A
GPIOB->ODR |=0x01<<2; //SEGMENTO B
GPIOB->ODR |=0x01<<3; //SEGMENTO C


Se definien los puertos que se utilizaran para habilitar cada display
PIOA->BSRR = (0x03<<16); 				//COLOCA 0 EN PA0 Y PA1

GPIOB->MODER &=~(1<<17); 				//PB8 SALIDA DEL SEGMENTO A
GPIOB->MODER &=~(1<<5); 				//PB2 SALIDA DEL SEGMENTO B
GPIOB->MODER &=~(1<<7); 				//PB3 SALIDA DEL SEGMENTO C
GPIOB->MODER &=~(1<<9); 				//PB4 SALIDA DEL SEGMENTO D
GPIOB->MODER &=~(1<<13);				//PB6 SALIDA DEL SEGMENTO E
GPIOB->MODER &=~(1<<15); 				//PB7 SALIDA DEL SEGMENTO F
GPIOB->MODER &=~(1<<19); 				//PB9 SALIDA DEL SEGMENTO G


Se habilita el reloj de los GPIOS que se usarán
RCC->IOPENR |=0x01<<0; 					//HABILITA RELOJ DE GPIOA
RCC->IOPENR |=0x01<<1; 					//HABILITA RELOJ DE GPIOB
RCC->IOPENR |=0x01<<2; 					//HABILITA RELOJ DE GPIOC


Para la comunicación serial se habilita el USART
USART2->BRR = (0xDA); 					//SETEA EL BAUD RATE
USART2->CR1 |=(1<<3);					//HABILITA TX
USART2->CR1 |=(1<<2); 					//HABILITA RX

La lógica de la calculadora fue que primero se ingresa el primer valor de la operación que se va a realizar, valor que esta en la varible valor1, luego a presionar la tecla numeral el valor del primer valor se guarda en la variable val. Luego entra al siguietne if esperando que se ingrese el segundo valor digitandolo en el keypad. Luego se debe indicar en el keypad la operación que se desea realizar siendo A una suma, B una resta y C una multiplicación. Al finalizar se puede presionar de nuevo el numeral para que borre todos los valores y regresa al estado inicial esperando que se ingrese el primer valor para empezar una nueva operación. 


Adjunto link de youtube mostrando el funcionamiento de la calculadora y explicación del funcionamiento del código. 
https://youtu.be/sWrV1EO2ZG0

