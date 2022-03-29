
### Tur tanimlama


```C
#include <stdio.h>

//tur tanimlama
typedef int tam_sayi;

int main() {
    
    tam_sayi a=10;
    printf("%d",a);
    
    return 0;
}
```


### Yapılar

```C
#include <stdio.h>

struct{
    char ogrenci_adi[50];
    int numara;
    int ders_notlari[2];
} ogrenci1, ogrenci2; //global tanimlama

//global tanimlamaya bu fonksiyondan da ulaşılabilir.
// void f(){
    
// }

int main() {
    printf("1. ogrencinin ad soyadini giriniz: ");
    scanf("%s", ogrenci1.ogrenci_adi);
    
    printf("1. ogrencinin numarasiniz giriniz: ");
    scanf("%d", &(ogrenci1.numara));

    printf("1. ogrencinin arasinav notunu giriniz: ");
    scanf("%d", &(ogrenci1.ders_notlari[0]));    
    
    printf("1. ogrencinin final notunu giriniz: ");
    scanf("%d", &(ogrenci1.ders_notlari[1]));

    printf("2. ogrencinin ad soyadini giriniz: ");
    scanf("%s", ogrenci2.ogrenci_adi); 
    
    printf("2. ogrencinin numarasiniz giriniz: ");
    scanf("%d", &(ogrenci2.numara));
    
    printf("2. ogrencinin arasinav notunu giriniz: ");
    scanf("%d", &(ogrenci2.ders_notlari[0]));    
    
    printf("2. ogrencinin final notunu giriniz: ");
    scanf("%d", &(ogrenci2.ders_notlari[1]));
    
    printf("Ogrenci adi: %s, numara: %d, arasinav: %d, final %d\n", ogrenci1.ogrenci_adi, ogrenci1.numara, ogrenci1.ders_notlari[0], ogrenci1.ders_notlari[1]);
    printf("Ogrenci adi: %s, numara: %d, arasinav: %d, final %d\n", ogrenci2.ogrenci_adi, ogrenci2.numara, ogrenci2.ders_notlari[0], ogrenci2.ders_notlari[1]);
        
    return 0;
}
```


```C
#include <stdio.h>

struct ogrenci{
    char ogrenci_adi[50];
    int numara;
    int ders_notlari[2];
};

int main() {
    //local tanimlama
    struct ogrenci ogrenci1, ogrenci2; 
    
    printf("1. ogrencinin ad soyadini giriniz: ");
    scanf("%s", ogrenci1.ogrenci_adi);
    
    // ....
        
    return 0;
}
```



```C
#include <stdio.h>
/*
struct{
    char ogrenci_adi[50];
    int numara;
    int ders_notlari[2];
}ogrenci1, ogrenci2; //global tanimlama

struct ogrenci{
    char ogrenci_adi[50];
    int numara;
    int ders_notlari[2];
}; //fonksiyonlar icinde local tanimlama yapilabilir

*/

// struct tur tanimlamasi
typedef struct{
    char ogrenci_adi[50];
    int numara;
    int ders_notlari[2];
} ogrenciler; //struct tur tanimlamasi

int main() {
    ogrenciler ogrenci1, ogrenci2;
    
    printf("1. ogrencinin ad soyadini giriniz: ");
    scanf("%s", ogrenci1.ogrenci_adi);
    
    printf("1. ogrencinin numarasiniz giriniz: ");
    scanf("%d", &(ogrenci1.numara));

    // ....
        
    return 0;
}
```


```C
#include <stdio.h>
#include <math.h>

typedef struct {
    float x;
    float y;
    float z;
} nokta;


int main() {
    nokta a,b;
    float uzaklik;
    a.x=10;
    a.y=8.9;
    a.z=14.8;
    
    b.x=5;
    b.y=9.1;
    b.z=3.6;
    
    uzaklik=sqrt(pow(a.x-b.x, 2)+pow(a.y-b.y, 2)+pow(a.z-b.z, 2));
    
    printf("a noktasi ile b noktasi arasindaki uzaklik: %f", uzaklik);
    
    return 0;
}
```


```C
#include <stdio.h>
#include <math.h>

typedef struct {
    float x;
    float y;
    float z;
} nokta;

float noktalar_arasi_uzaklik(nokta nokta1, nokta nokta2){
    return sqrt(pow(nokta1.x-nokta2.x, 2)+pow(nokta1.y-nokta2.y, 2)+pow(nokta1.z-nokta2.z, 2));    
}

int main() {
    nokta a,b;
    float uzaklik;
    a.x=10;
    a.y=8.9;
    a.z=14.8;
    
    b.x=5;
    b.y=9.1;
    b.z=3.6;
    uzaklik=noktalar_arasi_uzaklik(a,b);
    printf("a noktasi ile b noktasi arasindaki uzaklik: %f", uzaklik);
    return 0;
}
```




```C
#include <stdio.h>

typedef struct {
    float x;
    float y;    
} nokta;

typedef struct {
    nokta sol_ust;
    nokta sag_alt;
} dikdortgen;

int main() {
    float yukseklik;
    float genislik;
    dikdortgen a;
    
    a.sol_ust.x=2;
    a.sol_ust.y=5;
    
    a.sag_alt.x=7;
    a.sag_alt.y=3;
    
    genislik = a.sag_alt.x -a.sol_ust.x;
    yukseklik = a.sol_ust.y - a.sag_alt.y;
    
    printf("yukseklik: %f, genislik: %f", yukseklik, genislik);
    return 0;
}
```


```C
#include <stdio.h>

typedef struct{
    float reel;
    float imaj;
} karmasik;

int main() {
    
    karmasik a,b, toplam;
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);
    
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);
    
    toplam.reel = a.reel + b.reel;
    toplam.imaj = a.imaj + b.imaj;
    
    printf("karmasik sayilarin toplami: \n");
    printf("%f + i%f",toplam.reel,toplam.imaj);
    
    return 0;
}
```


```C
#include <stdio.h>

typedef struct karmasik_sayi{
    float reel;
    float imaj;
} karmasik;

karmasik karmasik_topla(karmasik x1, karmasik x2){
    karmasik sonuc;
    sonuc.reel=x1.reel+x2.reel;
    sonuc.imaj=x1.imaj+x2.imaj;
    return sonuc;
}

int main() {
    
    karmasik a, b, c;
    
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);

    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);
    
    c=karmasik_topla(a,b);
    
    printf("toplama islemi sonucu: %.2f+j%.2f",c.reel,c.imaj);
     
    return 0;
}
```


```C
#include <stdio.h>

typedef struct{
    float reel;
    float imaj;
} karmasik;

int main() {
    
    karmasik a,b, toplam;
    karmasik *p1, *p2;
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);
    
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);
    
    p1=&a;
    p2=&b;
    
    toplam.reel = (*p1).reel + (*p2).reel;
    toplam.imaj = (*p1).imaj + (*p2).imaj;
    
    printf("karmasik sayilarin toplami: \n");
    printf("%f + i%f",toplam.reel,toplam.imaj);
    
    return 0;
}
```


```C
#include <stdio.h>

typedef struct{
    float reel;
    float imaj;
} karmasik;

int main() {
    
    karmasik a,b, toplam;
    karmasik *p1, *p2;
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);
    
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);
    
    p1=&a;
    p2=&b;
    
    toplam.reel = p1->reel + p2->reel;
    toplam.imaj = p1->imaj + p2->imaj;
    
    printf("karmasik sayilarin toplami: \n");
    printf("%f + i%f",toplam.reel,toplam.imaj);
    
    return 0;
}
```


```C
#include <stdio.h>

typedef struct{
    float reel;
    float imaj;
} karmasik;

int main() {
    
    karmasik a,b, toplam;
    karmasik *p1, *p2, *p3;
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);
    
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);
    
    p1=&a;
    p2=&b;
    p3=&toplam;
    
    p3->reel = p1->reel + p2->reel;
    p3->imaj = p1->imaj + p2->imaj;
    
    printf("karmasik sayilarin toplami: \n");
    printf("%f + i%f",p3->reel, p3->imaj);
    
    return 0;
}
```


```C
#include <stdio.h>

typedef struct karmasik_sayi{
    float reel;
    float imaj;
} karmasik;


karmasik* karmasik_topla(karmasik *x1, karmasik *x2, karmasik *toplam){
    toplam->reel=x1->reel+x2->reel;
    toplam->imaj=x1->imaj+x2->imaj;
    return toplam;
}
int main() {    
    karmasik a, b, c;
    karmasik *pa, *pb, *pc;    
    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a.reel, &a.imaj);
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &b.reel, &b.imaj);    
    pa=&a;
    pb=&b;
    pc=&c;    
    pc=karmasik_topla(pa,pb,pc); // karmasik_topla(&a,&b)    
    printf("toplama islemi sonucu: %.2f+j%.2f\n",c.reel,c.imaj);
    printf("toplama islemi sonucu: %.2f+j%.2f\n",pc->reel,pc->imaj);
    
    return 0;
}
```


```C
#include <stdio.h>

typedef struct karmasik_sayi{
    float reel;
    float imaj;
} karmasik;

karmasik karmasik_topla(karmasik x1, karmasik x2){
    karmasik toplam;
    toplam.reel=x1.reel+x2.reel;
    toplam.imaj=x1.imaj+x2.imaj;
    return toplam;
}
int main() {    
    karmasik a[3];

    printf("birinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a[0].reel, &a[0].imaj);
    printf("ikinci karmasik sayiyi giriniz: ");
    scanf("%f%f", &a[1].reel, &a[1].imaj);    
    
    a[2]=karmasik_topla(a[0] ,a[1]);     
    printf("toplama islemi sonucu: %.2f+j%.2f\n",a[2].reel,a[2].imaj);

    return 0;
}
```


```C
#include <stdio.h>

typedef struct karmasik_sayi{
    float reel;
    float imaj;
} karmasik;

karmasik karmasik_topla(karmasik sayilar[], int n){
    karmasik toplam={0,0};
    int i;
    for(i=0;i<n;i++){
        toplam.reel += sayilar[i].reel;
        toplam.imaj += sayilar[i].imaj;
    }
    return toplam;
}
int main() {    
    karmasik a[10];
    karmasik sonuc;
    int i;
    
    printf("10 tane karmasik sayinin reel ve imajiner kisimlarini giriniz");
    for(i=0;i<10;i++)
        scanf("%f%f", &a[i].reel, &a[i].imaj);
    
    sonuc=karmasik_topla(a ,10);     
    printf("toplama islemi sonucu: %.2f+j%.2f\n",sonuc.reel,sonuc.imaj);    
    
    return 0;
}
```