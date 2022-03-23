```C
#define RCC_AHB1ENR (*((volatile int*)0x40023830))	
typedef struct{
	volatile int MODER;
	volatile int OTYPER;
	volatile int OSPEEDR;
	volatile int PUPDR;
	volatile int IDR;
	volatile int ODR;
} GPIO_Typedef;

int main(){
	volatile int i;
	GPIO_Typedef *GPIOD;
	GPIOD = (GPIO_Typedef*)0x40020C00;
	
	RCC_AHB1ENR |= 1<<3;
	
	GPIOD->MODER |= 1<<30;
	
	while(1){
		GPIOD->ODR |= 1<<15;
		for(i=0;i<1000000;i++);
		GPIOD->ODR &= ~(1<<15);
		for(i=0;i<1000000;i++);
	}
}
```


```C
#include "stm32f4xx.h"
int main(){
	volatile int i;
	RCC->AHB1ENR |= 1U<<3;
	GPIOD->MODER |= 1U<<24;
	while(1){
		GPIOD->ODR |= 1U<<12;
		for(i=0;i<1000000;i++);
		GPIOD->ODR &= ~(1U<<12);
		for(i=0;i<1000000;i++);
	}
}
```

```C
#include "stm32f4xx.h"
int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER12_0;
	while(1){
		GPIOD->ODR |= GPIO_ODR_OD12;
		for(i=0;i<1000000;i++);
		GPIOD->ODR &= ~GPIO_ODR_OD12;
		for(i=0;i<1000000;i++);
	}
}
```

```C
#include "stm32f4xx.h"
int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER12_0 | GPIO_MODER_MODER13_0;
	while(1){
		GPIOD->ODR |= GPIO_ODR_OD12 | GPIO_ODR_OD13;
		for(i=0;i<1000000;i++);
		GPIOD->ODR &= ~(GPIO_ODR_OD12 | GPIO_ODR_OD13);
		for(i=0;i<1000000;i++);
	}
}
```

```C
#include "stm32f4xx.h"
int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN | RCC_AHB1ENR_GPIOAEN;
	GPIOD->MODER |= GPIO_MODER_MODER12_0 | GPIO_MODER_MODER13_0;
	GPIOA->MODER &= ~GPIO_MODER_MODER0;
	while(1){
		if(GPIOA->IDR & GPIO_IDR_ID0){
			GPIOD->ODR |= GPIO_ODR_OD12 | GPIO_ODR_OD13;
			for(i=0;i<1000000;i++);
			GPIOD->ODR &= ~(GPIO_ODR_OD12 | GPIO_ODR_OD13);
			for(i=0;i<1000000;i++);
		}
	}
}
```