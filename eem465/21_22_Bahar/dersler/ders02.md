## Makro tanımlama

```C
#define PI 3.14
int main(){

    double yaricap=2.0, alan;
	alan=PI * yaricap * yaricap;  

}
 ``` 

Bir değişkenin n.bitten itibaren 2 bitlik kısmında işlem yapacağımızı var sayalım. Bu işlemleri aşağıdaki makrolar ile yapabiliriz.

```C
#define POS (12U)
#define MASK (0x3U<<POS)
#define MASK_0 (0x1U<<POS)
#define MASK_1 (0x2U<<POS)

int main(){
	
	int a= 0x12AF04BA;
	a = a | MASK;
	a= 0x12AF04BA;
	a= a | MASK_0;
	a= 0x12AF04BA;
	a= a | MASK_1;


}
 ``` 

## İşaretçiler

```C
int main(){
    
    int a=10, b=20;
	int *p;
	
	p=&a;
	*p = *p + 10;
	
	p=&b;
	*p = *p + 10;
    
    
}
 ``` 


## Tür dönüşümü
```C
int main(){
    
    double a=10.3;
    double tam, ondalik;
    
    tam = (int)a;
    ondalik = a-tam;
    
}
 ``` 

Sayısal bir değerin işaretçi türüne dönüşümü:

```C
int main(){
    
    int adres_verisi;
    adres_verisi = *((int*)0x40020400);
        
}
 ``` 

```C
int main(){
		(*(int *)0x40023830) = (*(int *)0x40023830) | (1<<3);
}
```

Tür dönüşümü, işaretçi ve makronun birlikte kullanılması:
```C
#define GPIOB_MODER (*((int*)0x40020400))

int main(){
    
    int adres_verisi;    
    adres_verisi = GPIOB_MODER;
        
}
 ``` 
 
## Tür tanımlama

```C
typedef unsigned char BOOL;

int main(){
    
    BOOL x;
    x=1;
    x=0;
        
}
 ```


## Yapılar

```C
#include <string.h>

struct calisan{
	char isim[50];
	int sicil;
	float maas;
};
int main(){
	struct calisan calisan1;
	//calisan1.isim="isim soyisim";
	strcpy(calisan1.isim, "isim soyisim");
	calisan1.sicil=1001;
	calisan1.maas=6000;
}
 ``` 


```C
#include <string.h>

struct calisan{
	char isim[50];
	int sicil;
	float maas;
};

int main(){
	struct calisan calisan1;
	struct calisan *p;
	//calisan1.isim="isim soyisim";
	p=&calisan1;
	strcpy((*p).isim,"isim soyisim");
	(*p).sicil=1001;
	(*p).maas=6000;
	
	strcpy(p->isim,"isim soyisim");
	p->maas=7000;
	p->sicil=1002;
	
}
 ``` 


```C
#include <string.h>

typedef struct {
    char isim[50];
    int sicil;
    float maas;
}calisan;

int main(){

    calisan calisan1, *p;
    
    strcpy(calisan1.isim, "isim soyisim");
    calisan1.maas=6571.7;
    calisan1.sicil=1254;
    
    p=&calisan1;

    (*p).maas=7500.1;
    (*p).sicil=1255;

    //veya işaretçi için ok operatörü kullanılabilir.
    
    p->maas=7900.1;
    p->sicil=1300;
    
}
 ``` 

