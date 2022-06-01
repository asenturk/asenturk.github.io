```C
#include "stm32f4xx.h"

volatile static double analog;

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	GPIOA->MODER |= GPIO_MODER_MODER1;
	
	RCC->APB2ENR |= RCC_APB2ENR_ADC1EN;
	
	ADC1->CR2 |= ADC_CR2_ADON;
	ADC1->CR2 |= ADC_CR2_CONT;
	ADC1->SQR3 |= ADC_SQR3_SQ1_0;
	
	ADC1->CR2 |= ADC_CR2_SWSTART;
	
	while(1){
		while(!(ADC1->SR & ADC_SR_EOC));
		analog = (ADC1->DR/4095.0)*3.3;
	}
}
```

```C
#include "stm32f4xx.h"

volatile static double analog[2];
volatile static int i=0;

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	GPIOA->MODER |= GPIO_MODER_MODER1 | GPIO_MODER_MODER3;
	
	RCC->APB2ENR |= RCC_APB2ENR_ADC1EN;
	
	ADC1->CR2 |= ADC_CR2_ADON;
	ADC1->CR2 |= ADC_CR2_CONT;
	ADC1->CR1 |= ADC_CR1_SCAN;
	ADC1->CR2 |= ADC_CR2_EOCS;
	ADC1->SMPR2 |= ADC_SMPR2_SMP1 | ADC_SMPR2_SMP3;
	ADC->CCR |= ADC_CCR_ADCPRE;
	ADC1->SQR1 |= ADC_SQR1_L_0;
	
	ADC1->SQR3 |= ADC_SQR3_SQ1_0; 
	ADC1->SQR3 |= ADC_SQR3_SQ2_1 | ADC_SQR3_SQ2_0;
	
	ADC1->CR2 |= ADC_CR2_SWSTART;
	
	while(1){
		while(!(ADC1->SR & ADC_SR_EOC));
		analog[i%2] = (ADC1->DR/4095.0)*3.3;
		i++;
	}	
}
```