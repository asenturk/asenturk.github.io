```C
#include "stm32f4xx.h"

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER13_0;
	
	SysTick->LOAD = 2000000;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		GPIOD->ODR |= GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		GPIOD->ODR &= ~GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
	}
}
```



```C
#include "stm32f4xx.h"

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER13_0;
	
	SysTick->LOAD = 2000000;
	SysTick->CTRL |= SysTick_CTRL_CLKSOURCE_Msk;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		GPIOD->ODR |= GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		GPIOD->ODR &= ~GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
	}
}
```



```C
#include "stm32f4xx.h"

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER13_0;
	
	SysTick->LOAD = 16000;
	SysTick->CTRL |= SysTick_CTRL_CLKSOURCE_Msk;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		
		if(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk){
			if(GPIOD->ODR & GPIO_ODR_OD13)
				GPIOD->ODR &= ~GPIO_ODR_OD13;
			else
				GPIOD->ODR |= GPIO_ODR_OD13;
		}	
	}
}
```



```C
#include "stm32f4xx.h"

void SysTick_Handler(void);
void SysTick_Handler(){
	if(GPIOD->ODR & GPIO_ODR_OD13)
			GPIOD->ODR &= ~GPIO_ODR_OD13;
		else
			GPIOD->ODR |= GPIO_ODR_OD13;
}

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER13_0;
	
	NVIC_EnableIRQ(SysTick_IRQn);
	
	SysTick->LOAD = 16000000;
	SysTick->CTRL |= SysTick_CTRL_CLKSOURCE_Msk;
	SysTick->CTRL |= SysTick_CTRL_TICKINT_Msk;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1);
}
```