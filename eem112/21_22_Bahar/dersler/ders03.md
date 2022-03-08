```C
#include <stdio.h>

void ayristir(float sayi, int *tam, float *ondalikli){
    *tam = (int)sayi;
    *ondalikli = sayi - *tam;
}

int main() {
    float x=5.4;
    int tam;
    float kesir;
    ayristir(x, &tam, &kesir);
    printf("%.2f sayisinin tam kismi: %d\n ondalikli kismi: %.2f",x, tam, kesir);
    
	return 0;
}
```

    5.40 sayisinin tam kismi: 5
     ondalikli kismi: 0.40


```C
#include <stdio.h>
void dizi_maks_min(int dizi[], int n, int *maks, int *min){
    int i;
    *maks=dizi[0];
    *min=dizi[0];
    for(i=1;i<n;i++){
        if( dizi[i] > *maks )
            *maks = dizi[i];
        if(dizi[i] < *min)
            *min=dizi[i];
    }
}

int main() {
    int a[]={3,5,7,3,2,7,9,4,3,5,1,5,-8,5,4,3,100,1};
    int eb, ek;
    //printf("%d %d %d",sizeof(a),sizeof(int),sizeof(a)/sizeof(int));
    dizi_maks_min(a, sizeof(a)/sizeof(int), &eb, &ek);
    printf("dizinin en buyuk sayisi: %d\n en kucuk sayisi: %d",eb, ek);
    
	return 0;
}
```

    dizinin en buyuk sayisi: 100
     en kucuk sayisi: -8


```C
#include <stdio.h>
void dizi_maks_min(int dizi[], int n, int *maks, int *min){
    int  *p;
    *maks=dizi[0];
    *min=dizi[0];
    p=dizi;
    for(p=dizi; p<dizi+n  ; p++){
        if( *p > *maks )
            *maks = *p;
        if(*p < *min)
            *min=*p;
    }
}

int main() {
    int a[]={3,5,7,3,2,7,9,4,3,5,1,5,-8,5,4,3,100,1};
    int eb, ek;
    //printf("%d %d %d",sizeof(a),sizeof(int),sizeof(a)/sizeof(int));
    dizi_maks_min(a, sizeof(a)/sizeof(int), &eb, &ek);
    printf("dizinin en buyuk sayisi: %d\n en kucuk sayisi: %d",eb, ek);
    
	return 0;
}
```

    dizinin en buyuk sayisi: 100
     en kucuk sayisi: -8


```C
#include <stdio.h>
void dizi_maks_min(int dizi[], int n, int *maks, int *min){
    int  i;
    *maks=dizi[0];
    *min=dizi[0];
    
    for(i=1;i<n;i++){
        if( *(dizi+i) > *maks )
            *maks = *(dizi+i);
        if(*(dizi+i) < *min)
            *min=*(dizi+i);
    }
}

int main() {
    int a[]={3,5,7,3,2,7,9,4,3,5,1,5,-8,5,4,3,100,1};
    int eb, ek;
    //printf("%d %d %d",sizeof(a),sizeof(int),sizeof(a)/sizeof(int));
    dizi_maks_min(a, sizeof(a)/sizeof(int), &eb, &ek);
    printf("dizinin en buyuk sayisi: %d\n en kucuk sayisi: %d",eb, ek);
    
	return 0;
}
```

    dizinin en buyuk sayisi: 100
     en kucuk sayisi: -8


```C
#include <stdio.h>

int *buyuk(int *sayi1, int *sayi2){
    if(*sayi1 > *sayi2)
        return sayi1;
    return sayi2;
    
}
int main() {
    
    int a=20, b=15;
    int *p;
    p=buyuk(&a, &b);
    
    printf("buyuk sayi: %d", *p);
    
	return 0;
}
```

    buyuk sayi: 20


```C
#include <stdio.h>

int *buyuk(int *sayi1, int *sayi2){
    if(*sayi1 > *sayi2)
        return sayi1;
    return sayi2;
    
}
int main() {
    
    int a=20, b=15;
    
    printf("buyuk sayi: %d", *buyuk(&a, &b));
    
	return 0;
}
```

    buyuk sayi: 20


```C
#include <stdio.h>

int *buyuk(const int *sayi1, const int *sayi2){
    //parametrelerde degisiklik istenmiyorsa const kullanılabilir.
    
    //bu islem const kelimesinden dolayı hatalı.
    //*sayi2=50;
    if(*sayi1 > *sayi2)
        return sayi1;
    return sayi2;
    
}
int main() {
    
    int a=20, b=15;
    
    printf("buyuk sayi: %d", *buyuk(&a, &b));
    
	return 0;
}
```

    buyuk sayi: 20


```C
#include <stdio.h>
//swap
void yer_degistir(int *sayi1, int *sayi2){
    int x;
    x=*sayi1;
    *sayi1= *sayi2;
    *sayi2=x;
    
}
int main() {
    
    int a=10, b=20;
    yer_degistir(&a, &b);
    printf("a:%d b:%d",a,b);
    
	return 0;
}
```

    a:20 b:10


```C
#include <stdio.h>

int main() {
    
    int a[]={2,4,6,8,10,12,14};
    int *p;
    p=a;
    printf("%d \n",*p);
    printf("%d \n",*a);"cv"
    printf("%d \n",*p+1);
    printf("%d \n",*(p+1));
    printf("%d \n",*(p+3));
    printf("%d \n",*(a+4));
    
	return 0;
}
```

    2 
    2 
    3 
    4 
    8 
    10 



```C
#include <stdio.h>
#define N 10
int main() {
    
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int toplam=0, i;
    for(i=0;i<N;i++)
        toplam += a[i];
    printf("toplam: %d",toplam);
     
	return 0;
}
```

    toplam: 110


```C
#include <stdio.h>
#define N 10
int main() {
    
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int toplam=0;
    int *p;
    for(p=a;p<a+N;p++)
        toplam += *p;
    printf("toplam: %d",toplam);
     
	return 0;
}
```

    toplam: 110


```C
#include <stdio.h>
#define N 10
int main() {
    
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int toplam=0, i;

    for(i=0 ;i<N;i++)
        toplam += *(a+i);
    printf("toplam: %d",toplam);
     
	return 0;
}
```

    toplam: 110


```C
#include <stdio.h>
#define N 10
int main() {
    //diziyi tersine cevirme
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int b[N];
    int i;

    for(i=N-1 ;i>=0; i--)
        b[N-i-1] = a[i];
    
    for(i=0;i<N;i++)
        printf("%d ",b[i]);    
     
	return 0;
}
```

    20 18 16 14 12 10 8 6 4 2 


```C
#include <stdio.h>
#define N 10
int main() {
    //diziyi tersine cevirme
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int b[N];
    int *p, i;
    
    for(p=a+N-1, i=0; p>=a; p--,i++)
        b[i] = *p;
    
    for(i=0;i<N;i++)
        printf("%d ",b[i]);    
     
	return 0;
}
```

    20 18 16 14 12 10 8 6 4 2 


```C
#include <stdio.h>
#define N 10
int main() {
    //diziyi tersine cevirme
    int a[N]={2,4,6,8,10,12,14,16,18,20};
    int b[N];
    int *p, *q;
    
    for(p=a+N-1, q=b; p>=a; p--,q++)
        *q = *p;
    
    for(p=b;p<b+N;p++)
        printf("%d ",*p);    
     
	return 0;
}
```

    20 18 16 14 12 10 8 6 4 2 


