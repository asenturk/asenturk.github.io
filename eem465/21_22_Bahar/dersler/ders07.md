```C
#include "stm32f4xx.h"
int main(){
	
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOCEN;
	GPIOC->MODER |= GPIO_MODER_MODER14_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_TIM6EN;
	
	TIM6->PSC = 15;
	TIM6->ARR = 10000;
	TIM6->CR1 |= TIM_CR1_CEN;

	while(1){
		GPIOC->ODR |= GPIO_ODR_OD14;
		while(!(TIM6->SR & TIM_SR_UIF));
		TIM6->SR &= ~TIM_SR_UIF;
		
		GPIOC->ODR &= ~GPIO_ODR_OD14;
		while(!(TIM6->SR & TIM_SR_UIF));
		TIM6->SR &= ~TIM_SR_UIF;
	}
}
```


```C
#include "stm32f4xx.h"
int main(){
	
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOCEN;
	GPIOC->MODER |= GPIO_MODER_MODER14_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_TIM6EN;
	
	TIM6->PSC = 15;
	TIM6->ARR = 1000;
	TIM6->CR1 |= TIM_CR1_CEN;

	while(1){
		if(TIM6->SR & TIM_SR_UIF){
			TIM6->SR &= ~TIM_SR_UIF;
			if(GPIOC->ODR & GPIO_ODR_OD14)
				GPIOC->ODR &= ~GPIO_ODR_OD14;
			else
				GPIOC->ODR |= GPIO_ODR_OD14;	
		}
	}
}
``` 

```C
#include "stm32f4xx.h"
void TIM6_DAC_IRQHandler(void);
void TIM6_DAC_IRQHandler(void){
	TIM6->SR &= ~TIM_SR_UIF;
	
	if(GPIOE->ODR & GPIO_ODR_OD11)
		GPIOE->ODR &= ~GPIO_ODR_OD11;
	else
		GPIOE->ODR |= GPIO_ODR_OD11;	
}

int main(){

	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOEEN;
	GPIOE->MODER |= GPIO_MODER_MODER11_0;
	
	RCC->APB1ENR |=RCC_APB1ENR_TIM6EN;
	
	NVIC_EnableIRQ(TIM6_DAC_IRQn)
	TIM6->DIER |= TIM_DIER_UIE;
	TIM6->PSC=1;
	TIM6->ARR = 99;
	TIM6->CR1 |= TIM_CR1_CEN;
	
	while(1){
	}
}
```