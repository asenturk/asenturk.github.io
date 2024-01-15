```C
#include <stdio.h>

double ortalama3(double a, double b, double c){
    // double a, double b, double c bu fonksiyonun parametreleridir.
    //fonksiyonun önündeki ifade dönen değerin türüdür.
    //double ortalama3(double a, double b, double c) veya
    //double ortalama3(double, double, double) fonksiyonun prototipidir.
    return (a+b+c)/3;
}
int main() {
    double x,y,z;
    double ort;
    printf("ortalama islemi icin 3 deger giriniz:");
    scanf("%lf %lf %lf",&x,&y,&z);
    printf("sayilarin ortalamasi: %lf\n", ortalama3(x,y,z));
    printf("sayilarin ortalamasi: %lf\n", ortalama3(1,5,6));
    ort=ortalama3(y,z,x);
    printf("sayilarin ortalamasi: %lf\n", ort);
    return 0;
}
```

    ortalama islemi icin 3 deger giriniz:

     20 12 14


    sayilarin ortalamasi: 15.333333
    sayilarin ortalamasi: 4.000000
    sayilarin ortalamasi: 15.333333



```C
#include <stdio.h>

double ortalama3(double a, double b, double c){
    double sayilarin_ortalamasi;
    sayilarin_ortalamasi = (a+b+c)/3;
    return sayilarin_ortalamasi;
}
int main() {
    double x,y,z;
    double ort;
    printf("ortalama islemi icin 3 deger giriniz:");
    scanf("%lf %lf %lf",&x,&y,&z);
    printf("sayilarin ortalamasi: %lf\n", ortalama3(x,y,z));
    printf("sayilarin ortalamasi: %lf\n", ortalama3(1,5,6));
    ort=ortalama3(y,z,x);
    printf("sayilarin ortalamasi: %lf\n", ort);
    return 0;
}
```

    ortalama islemi icin 3 deger giriniz:

     1 5 7


    sayilarin ortalamasi: 4.333333
    sayilarin ortalamasi: 4.000000
    sayilarin ortalamasi: 4.333333



```C
#include <stdio.h>

double ortalama3(double a, double b, double c){

    return (a+b+c)/3;
}
int main() {
    double x,y,z,a=10,b=20;
    printf("ortalama islemi icin 3 deger giriniz:");
    scanf("%lf %lf %lf",&x,&y,&z);
    
    b += a+ortalama3(x,y,z);
    printf("islemin sonucu: %lf", b);
    return 0;
}
```

    ortalama islemi icin 3 deger giriniz:

     10 20 12


    islemin sonucu: 44.000000


```C
#include <stdio.h>

double ortalama3(double a, double b, double c){

    return (a+b+c)/3;
}
int main() {
    double x,y,z;
    printf("ortalama islemi icin 3 deger giriniz:");
    scanf("%lf %lf %lf",&x,&y,&z);
    
    if(ortalama3(x,y,z)>0)
        printf("sayilarin ortalamasi pozitiftir.");
    else
        printf("sayilarin ortalamasi 0 veya negatiftir.");
    
    return 0;
}
```

    ortalama islemi icin 3 deger giriniz:

     -9 2 4


    sayilarin ortalamasi 0 veya negatiftir.


```C
#include <stdio.h>
void sayac_bilgisi(int i){
    printf("sayacin degeri: %d\n",i);
}
int main() {
    int sayac;
    for(sayac=0;sayac<10;sayac++)
        sayac_bilgisi(sayac);   
    return 0;
}
```

    sayacin degeri: 0
    sayacin degeri: 1
    sayacin degeri: 2
    sayacin degeri: 3
    sayacin degeri: 4
    sayacin degeri: 5
    sayacin degeri: 6
    sayacin degeri: 7
    sayacin degeri: 8
    sayacin degeri: 9



```C
#include <stdio.h>
void selamlama(void){
    printf("merhaba ");
}
int main() {
    int sayac;
    for(sayac=0;sayac<10;sayac++)
        selamlama();   
    return 0;
}
```

    merhaba merhaba merhaba merhaba merhaba merhaba merhaba merhaba merhaba merhaba 


```C
#include <stdio.h>
int sayi_al_ve_topla(void){
    int a,b;
    printf("iki deger giriniz: ");
    scanf("%d %d",&a,&b);
    return a+b;
}
int main() {
    printf("%d", sayi_al_ve_topla());
    return 0;
}
```

    iki deger giriniz: 

     10 20


    30


```C
#include <stdio.h>
int sayi_al_ve_topla(void){
    int a,b;
    printf("iki deger giriniz: ");
    scanf("%d %d",&a,&b);
    printf("toplam: %d\n",a+b);
    return a+b;
}
int main() {
    int x=10,y=20,z;
    z=x+y+sayi_al_ve_topla();
    printf("%d",z);
    
    
    return 0;
}
```

    iki deger giriniz: 

     10 20


    toplam: 30
    60


```C
#include <stdio.h>
int main() {
    int a=10, uzunluk;
    uzunluk=printf("a degiskeninin degeri: %d\n",a);
    printf("bir onceki metnin uzunlugu: %d", uzunluk);
    return 0;
}
```

    a degiskeninin degeri: 10
    bir onceki metnin uzunlugu: 26


```C
#include <stdio.h>
int asal_mi(int sayi){
    int i;
    if(sayi<2)
        return 0;
    if(sayi==2)
        return 1;
    
    for(i=2;i<sayi;i++)
        if(sayi%i==0)
            return 0;
    return 1;
}

int main() {
    int n;
    printf("bir sayi giriniz: ");
    scanf("%d",&n);
//     if(asal_mi(n)==1)
    if(asal_mi(n))
        printf("girilen sayi asaldir.");
    else
        printf("girilen sayi asal degildir.");
    return 0;
}
```

    bir sayi giriniz: 

     101


    girilen sayi asaldir.


```C
#include <stdio.h>

//eger fonksiyon ana fonksiyonun altinda ise
//ana fonksiyonun ustune fonk. prototipini yazmaniz gerekir.

// int asal_mi(int sayi);
//veya
int asal_mi(int);

int main() {
    int n;
    printf("bir sayi giriniz: ");
    scanf("%d",&n);
//     if(asal_mi(n)==1)
    if(asal_mi(n))
        printf("girilen sayi asaldir.");
    else
        printf("girilen sayi asal degildir.");
    return 0;
}

int asal_mi(int sayi){
    int i;
    if(sayi<2)
        return 0;
    if(sayi==2)
        return 1;
    
    for(i=2;i<sayi;i++)
        if(sayi%i==0)
            return 0;
    return 1;
}
```

    bir sayi giriniz: 

     1001


    girilen sayi asal degildir.


```C
#include <stdio.h>

//eger fonksiyon ana fonksiyonun altinda ise
//ana fonksiyonun ustune fonk. prototipini yazmaniz gerekir.

// int asal_mi(int sayi);
//veya
int asal_mi(int);
void sonuc_yazidir(int x);

int main() {
    int n;
    printf("bir sayi giriniz: ");
    scanf("%d",&n);
    sonuc_yazidir(n);
    
    return 0;
}

int asal_mi(int sayi){
    int i;
    if(sayi<2)
        return 0;
    if(sayi==2)
        return 1;
    
    for(i=2;i<sayi;i++)
        if(sayi%i==0)
            return 0;
    return 1;
}

void sonuc_yazidir(int x){
    if(asal_mi(x))
        printf("girilen sayi asaldir.");
    else
        printf("girilen sayi asal degildir.");
}
```

    bir sayi giriniz: 

     101


    girilen sayi asaldir.


```C
#include <stdio.h>
#define N 10
int dizi_topla(int a[], int boyut);
int main() {
    int x[N], i;
    printf("dizi icin %d deger giriniz: ", N);
    for(i=0;i<N;i++)
        scanf("%d", &x[i]);
    printf("dizinin elemanlarinin toplami: %d",dizi_topla(x, N));
    
    return 0;
}
int dizi_topla(int a[], int boyut){
    int toplam=0,i;
    for(i=0;i<boyut;i++)
        toplam += a[i];
    return toplam;
}


```

    dizi icin 10 deger giriniz: 

     2 1 4 5 7 9 4 5 1 2


    dizinin elemanlarinin toplami: 40


```C
#include <stdio.h>
#define N 10
void diziye_deger_ata(int dizi[], int boyut,  int atanacak_deger);
void dizi_yazdir(int x[], int n);
int main() {
    int x[5], deger;
    printf("dizinin elemanlarina ayni sayiyi atamak icin deger giriniz:");
    scanf("%d",&deger);
    diziye_deger_ata(x, 5, deger);
    dizi_yazdir(x, 5);    
    return 0;
}
void diziye_deger_ata(int dizi[], int boyut,  int atanacak_deger){
    int i;
    for(i=0;i<boyut;i++)
        dizi[i]=atanacak_deger;
}
void dizi_yazdir(int x[], int n){
    int i;
    for(i=0;i<n;i++)
        printf("%d ",x[i]);
}
```

    dizinin elemanlarina ayni sayiyi atamak icin deger giriniz:

     10


    10 10 10 10 10 


```C
#include <stdio.h>
#define N 5
#define M 4
int dizi_topla(int x[][M], int boyut);
int main() {
    
    int a[N][M],i,j;
    printf("a dizisine degerler giriniz: ");
    for(i=0;i<N;i++)
        for(j=0;j<M;j++)
            scanf("%d", &a[i][j]);
    
    printf("dizinin elemanlarinin toplami: %d", dizi_topla(a, sizeof(a)/sizeof(a[0])));
    return 0;
}

int dizi_topla(int x[][M], int boyut){
    int toplam=0,i,j;
    for(i=0;i<boyut;i++)
        for(j=0;j<M;j++)
            toplam += x[i][j];
    return toplam;
}

```

    a dizisine degerler giriniz: 

     2 6 6 8 7 6 8 4 8 9 5 4 4 5 7 2 9 4 6 4


    dizinin elemanlarinin toplami: 114


```C
#include <stdio.h>

int kontrol_pozitif(int n){
    if(n>0)
        return 1;
    return 0;
}
int main() {
    int x;
    printf("bir sayi giriniz: ");
    scanf("%d",&x);
    if(kontrol_pozitif(x))
        printf("sayi pozitiftir.");
    
    return 0;
}



```

    bir sayi giriniz: 

     5


    sayi pozitiftir.


```C
#include <stdio.h>

int kontrol_pozitif(int n){
    return n>0 ? 1 : 0; 
}
int main() {
    int x;
    printf("bir sayi giriniz: ");
    scanf("%d",&x);
    if(kontrol_pozitif(x))
        printf("sayi pozitiftir.");
    
    return 0;
}



```

    bir sayi giriniz: 

     10


    sayi pozitiftir.


```C
#include <stdio.h>

void pozitif_yaz(int n){
    if(n<=0)
        return;
    printf("sayi: %d",n);
}

int main() {
    int x;
    printf("bir sayi giriniz: ");
    scanf("%d",&x);
    pozitif_yaz(x);
    
    return 0;
}



```

    bir sayi giriniz: 

     10


    sayi: 10


```C
#include <stdio.h>

int main() {
    int sayi, kaynak_taban, hedef_taban;
    printf("sayi hangi tabanda");
    scanf("%d", &kaynak_taban);
    
    switch(kaynak_taban){
        case 8:
            printf("8 tabaninda sayiyi giriniz:");
            scanf("%o",&sayi);
            break;
        case 10:
            printf("10 tabaninda sayiyi giriniz:");
            scanf("%d",&sayi);
            break;    
        case 16:
            printf("16 tabaninda sayiyi giriniz:");
            scanf("%x",&sayi);
            break;
        default:
            printf("hatali taban degeri girdiniz");
            return 1;
    }
    printf("cevrilece sayi tabani");
    scanf("%d", &hedef_taban);
    switch(hedef_taban){
        case 8:
            printf("8 tabaninda sayiyi: %o", sayi);
            
            break;
        case 10:
            printf("10 tabaninda sayiyi: %d", sayi);
            
            break;    
        case 16:
            printf("16 tabaninda sayiyi: %X", sayi);
            break;
        default:
            printf("hatali taban degeri girdiniz");
            return 1;
    }

    
    return 0;
}



```

    sayi hangi tabanda

     10


    10 tabaninda sayiyi giriniz:

     161


    cevrilece sayi tabani

     16


    16 tabaninda sayiyi: A1


```C

```
