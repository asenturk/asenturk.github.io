```C
#include "stm32f4xx.h"

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOEEN;
	GPIOE->MODER |= GPIO_MODER_MODER11_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_TIM6EN;
	TIM6->PSC = 15;
	TIM6->ARR = 1000;
	TIM6->CR1 |= TIM_CR1_CEN;
	
	while(1){
		GPIOE->ODR |= GPIO_ODR_OD11;
		while(!(TIM6->SR & TIM_SR_UIF));
		TIM6->SR &= ~TIM_SR_UIF;
		
		GPIOE->ODR &= ~GPIO_ODR_OD11;
		while(!(TIM6->SR & TIM_SR_UIF));
		TIM6->SR &= ~TIM_SR_UIF;
	}
}

```

```C
#include "stm32f4xx.h" 

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOEEN;
	GPIOE->MODER |= GPIO_MODER_MODER11_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_TIM6EN;
	TIM6->PSC = 31;
	TIM6->ARR = 1000;
	TIM6->CR1 |= TIM_CR1_CEN;
	
	while(1){
		if(TIM6->SR & TIM_SR_UIF){
			TIM6->SR &= ~TIM_SR_UIF;
			
			if(GPIOE->ODR & GPIO_ODR_OD11)
				GPIOE->ODR &= ~GPIO_ODR_OD11;
			else
				GPIOE->ODR |= GPIO_ODR_OD11;	
		}
	}
}
```

```C
#include "stm32f4xx.h"   
void TIM6_DAC_IRQHandler(void);
void TIM6_DAC_IRQHandler(){
	TIM6->SR &= ~TIM_SR_UIF;
			
	if(GPIOE->ODR & GPIO_ODR_OD11)
		GPIOE->ODR &= ~GPIO_ODR_OD11;
	else
		GPIOE->ODR |= GPIO_ODR_OD11;	
}
int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOEEN;
	GPIOE->MODER |= GPIO_MODER_MODER11_0;
	
	RCC->APB1ENR |= RCC_APB1ENR_TIM6EN;
	TIM6->PSC = 31;
	TIM6->ARR = 5000;
	TIM6->DIER |= TIM_DIER_UIE;
	NVIC_EnableIRQ(TIM6_DAC_IRQn);
	TIM6->CR1 |= TIM_CR1_CEN;	
	while(1){
	}
}
```