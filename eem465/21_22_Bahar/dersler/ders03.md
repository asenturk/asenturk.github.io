```C
#define RCC_AHB1ENR (*((int*)0x40023830))

typedef struct{
	int X;
	int Y;
	int Z;
} GPIO_type;
int main(){
	GPIO_type *p;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<2);
	
	p = (GPIO_type*)0x40020800;
	p->X =  p->X | 1 <<5; 
	p->Y =  p->Y | 1 <<15;
	p->Z =  p->Z | 1 <<15;
}
```


```C
int main(){
	int RCC_AHB1ENR_adres, *RCC_AHB1ENR;
	int GPIOD_MODER_adres, *GPIOD_MODER;
	int GPIOD_ODR_adres, *GPIOD_ODR;
	
	RCC_AHB1ENR_adres=0x40023830;
	GPIOD_MODER_adres=0x40020C00;
	GPIOD_ODR_adres=0x40020C14;
	
	RCC_AHB1ENR = (int*)RCC_AHB1ENR_adres;
	GPIOD_MODER = (int*)GPIOD_MODER_adres;
	GPIOD_ODR = (int*)GPIOD_ODR_adres;
	
	*RCC_AHB1ENR = *RCC_AHB1ENR | (1<<3);
	*GPIOD_MODER = *GPIOD_MODER | (1<<26);
	*GPIOD_ODR = *GPIOD_ODR | (1<<13);
}
```



```C
int main(){
	volatile int RCC_AHB1ENR_adres, *RCC_AHB1ENR;
	volatile int GPIOD_MODER_adres, *GPIOD_MODER;
	volatile int GPIOD_ODR_adres, *GPIOD_ODR;
	
	RCC_AHB1ENR_adres=0x40023830;
	GPIOD_MODER_adres=0x40020C00;
	GPIOD_ODR_adres=0x40020C14;
	
	RCC_AHB1ENR = (volatile int*)RCC_AHB1ENR_adres;
	GPIOD_MODER = (volatile int*)GPIOD_MODER_adres;
	GPIOD_ODR = (volatile int*)GPIOD_ODR_adres;
	
	*RCC_AHB1ENR = *RCC_AHB1ENR | (1<<3);
	*GPIOD_MODER = *GPIOD_MODER | (1<<26);
	*GPIOD_ODR = *GPIOD_ODR | (1<<13);
}
```

```C
#define RCC_AHB1ENR (*((volatile int*)0x40023830))
#define GPIOD_MODER (*((volatile int*)0x40020C00))
#define GPIOD_ODR (*((volatile int*)0x40020C14))

int main(){
	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | (1<<26);
	while(1){
	GPIOD_ODR = GPIOD_ODR | (1<<13);
	for(i=0;i<1000000;i++);	
	GPIOD_ODR = GPIOD_ODR & ~(1<<13);
	for(i=0;i<1000000;i++);
	}
}
```

```C
#define RCC_AHB1ENR (*((volatile int*)0x40023830))
#define GPIOD_MODER (*((volatile int*)0x40020C00))
#define GPIOD_ODR (*((volatile int*)0x40020C14))

int main(){
	volatile int i;
	RCC_AHB1ENR |=  (1<<3);
	GPIOD_MODER |=  (1<<30);
	while(1){
	GPIOD_ODR |=  (1<<15);
	for(i=0;i<1000000;i++);	
	GPIOD_ODR &= ~(1<<15);
	for(i=0;i<1000000;i++);
	}
}
```


```C
#define RCC_AHB1ENR (*((volatile int*)0x40023830))
#define GPIOD_MODER (*((volatile int*)0x40020C00))
#define GPIOD_ODR (*((volatile int*)0x40020C14))

int main(){
	volatile int i;
	int pin=12;
	RCC_AHB1ENR |=  (1<<3);
	GPIOD_MODER |=  (1<< pin*2);
	while(1){
	GPIOD_ODR |=  (1<<pin);
	for(i=0;i<1000000;i++);	
	GPIOD_ODR &= ~(1<<pin);
	for(i=0;i<1000000;i++);
	}
}
```

```C
#define RCC_AHB1ENR (*((volatile int*)0x40023830))
#define GPIOD_MODER (*((volatile int*)0x40020C00))
#define GPIOD_ODR (*((volatile int*)0x40020C14))

int main(){
	volatile int i;
	RCC_AHB1ENR |=  (1<<3);
	GPIOD_MODER |=  (0x55<< 24);
	while(1){
	GPIOD_ODR |=  (0xF<<12);
	for(i=0;i<1000000;i++);	
	GPIOD_ODR &= ~(0xF<<12);
	for(i=0;i<1000000;i++);
	}
}
```