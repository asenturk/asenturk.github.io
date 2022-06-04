```C
#include "stm32f4xx.h"

volatile static char a[]="abcdefghijkl\n";
volatile static int i=0, j;

int main(){
	RCC->AHB1ENR |=RCC_AHB1ENR_GPIOAEN;
	GPIOA->MODER |= GPIO_MODER_MODER2_1;
	GPIOA->AFR[0] |= GPIO_AFRL_AFRL2_2 |
					GPIO_AFRL_AFRL2_1 |
					GPIO_AFRL_AFRL2_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_USART2EN;
	
	USART2->BRR = 0X683;
	USART2->CR1 |= USART_CR1_TE;
	USART2->CR1 |= USART_CR1_UE;
	
	while(1){
		USART2->DR= a[i++ % 14]  ;
		while(!(USART2->SR & USART_SR_TXE));
		while(!(USART2->SR & USART_SR_TC));
		for(j=0;j<1000000;j++);	
	
	}
}
```