```C
#include "stm32f4xx.h"
volatile static int pin=15;

void EXTI0_IRQHandler(void);
void EXTI0_IRQHandler(){
	EXTI->PR |= EXTI_PR_PR0;
	GPIOD->ODR &= ~(1U << pin);
	if(pin==15)
		pin=14;
	else
		pin=15;
}

int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN | RCC_AHB1ENR_GPIOAEN;
	GPIOD->MODER |= GPIO_MODER_MODER15_0 | GPIO_MODER_MODER14_0;
	
	NVIC_EnableIRQ(EXTI0_IRQn);
	SYSCFG->EXTICR[0] &= ~SYSCFG_EXTICR1_EXTI0;
	EXTI->IMR |= EXTI_IMR_MR0;
	EXTI->RTSR |= EXTI_RTSR_TR0;
			
	while(1){
			GPIOD->ODR |= 1 << pin;
			for(i=0;i<1000000;i++);
			GPIOD->ODR &= ~(1U << pin);
			for(i=0;i<1000000;i++);	
	}
}

```




```C
#include "stm32f4xx.h"
volatile static unsigned int sayac=0;
void EXTI0_IRQHandler(void);
void EXTI0_IRQHandler(){
	EXTI->PR |= EXTI_PR_PR0;
	sayac++;
	GPIOD->ODR &= ~(0xFU<<12);
	GPIOD->ODR |= (sayac%16)<<12;
	
}
void gpio_init(void);
void gpio_init(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN | RCC_AHB1ENR_GPIOAEN;
	GPIOD->MODER |= GPIO_MODER_MODER12_0 | GPIO_MODER_MODER13_0
						| GPIO_MODER_MODER14_0 | GPIO_MODER_MODER15_0;

}
void exti_init(void);
void exti_init(){
	NVIC_EnableIRQ(EXTI0_IRQn);
	EXTI->IMR |= EXTI_IMR_MR0;
	EXTI->RTSR |= EXTI_RTSR_TR0;
}

int main(){
	gpio_init();
	exti_init();
	while(1);
}

```