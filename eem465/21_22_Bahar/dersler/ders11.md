```C
#include "stm32f4xx.h"

int main(){
	RCC->CR |= RCC_CR_HSEON;
	while(!(RCC->CR & RCC_CR_HSERDY));
	RCC->CFGR |= RCC_CFGR_SW_0;
	
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOCEN;
	GPIOC->MODER |= GPIO_MODER_MODER3_0;
	
	SysTick->LOAD = 2000;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		GPIOC->ODR |= GPIO_ODR_OD3;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		GPIOC->ODR &= ~GPIO_ODR_OD3;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
	}
}
```