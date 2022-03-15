```C
#include <stdio.h>

int main() {
    int uzunluk=0;
    char metin[]="bu bir stringdir.";
    char *p;
    for(p=metin; *p != '\0'; p++)
        uzunluk++;
	
    printf("%d", uzunluk);
    return 0;
}
```
    17


```C
#include <stdio.h>

int str_uzunluk(char *str){
    int n;
    for(n=0; *str!='\0'; str++)
        n++;
    return n;  
}
int main() {
    char metin[]="bu bir stringdir.";
    
    printf("uzunluk: %d ",str_uzunluk(metin)); 
	return 0;
}
```
    uzunluk: 17 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n;
    for(n=0; *str!='\0'; str++, n++);     
    return n;
    
}
int main() {
    char metin[]="bu bir stringdir..";
    
    printf("uzunluk: %d ",str_uzunluk(metin));    
	return 0;
}
```
    uzunluk: 18 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n;
    for(n=0; *str; str++, n++);    
    return n;
}
int main() {
    char metin[]="bu bir stringdir...";
    
    printf("uzunluk: %d ",str_uzunluk(metin));
	return 0;
}
```
    uzunluk: 19 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n=0;
    for( ; *str++; )
        n++;
    return n; 
}
int main() {
    char metin[]="bu bir stringdir....";
    
    printf("uzunluk: %d ",str_uzunluk(metin));
	return 0;
}
```
    uzunluk: 20 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n=0;
    while(*str != '\0'){
        n++;
        str++;
    }    
    return n; 
}
int main() {
    char metin[]="bu bir stringdir.....";
    
    printf("uzunluk: %d ",str_uzunluk(metin));  
	return 0;
}
```

    uzunluk: 21 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n=0;
    while(*str){
        n++;
        str++;
    }
    return n; 
}
int main() {
    char metin[]="bu bir stringdir......";
    
    printf("uzunluk: %d ",str_uzunluk(metin));
	return 0;
}
```

    uzunluk: 22 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    int n=0;
    while(*str++)
        n++;

    return n;    
}
int main() {
    char metin[]="bu bir stringdir.......";
    
    printf("uzunluk: %d ",str_uzunluk(metin));
	return 0;
}
```
    uzunluk: 23 


```C
#include <stdio.h>

int str_uzunluk(const char *str){
    const char *p=str;
    while(*str) str++;
    
    return str-p;  
}
int main() {
    char metin[]="bu bir stringdir........";
    
    printf("uzunluk: %d ",str_uzunluk(metin)); 
	return 0;
}
```
    uzunluk: 24 


```C
#include <stdio.h>

int main() {
    char str1[]="birinci string.";
    char str2[30];
    char *p, *q;
    for(p=str1, q=str2; *p!='\0'; p++, q++)
        *q=*p;
    *q='\0';
    printf("%s", str2);

	return 0;
}
```
    birinci string.


```C
#include <stdio.h>

char *str_kopyala(char *kaynak, char *hedef){
    char *p;
    p=hedef;
    while(*kaynak!='\0'){
        *hedef=*kaynak;
        hedef++;
        kaynak++;
    }
    *hedef='\0';
    return p;
}


int main() {
    char str1[]="birinci string..";
    char str2[30];
    
    printf("%s", str_kopyala(str1, str2));

	return 0;
}
```
    birinci string..


```C
#include <stdio.h>

int main() {
    char a[]="birinci string. ";
    char b[]="ikinci string.";
    char c[35];
    char *p1, *p2;
    for(p1=a, p2=c; *p1!='\0'; p1++, p2++)
        *p2=*p1;
    
    for(p1=b; *p1!='\0'; p1++, p2++)
        *p2=*p1;
    *p2='\0';
    
    printf("%s", c);

	return 0;
}
```

    birinci string. ikinci string.


```C
#include <stdio.h>

char *str_birlestir(char *kaynak1, char *kaynak2, char *hedef){
    char *p=hedef;
    while(*kaynak1 != '\0'){
        *hedef = *kaynak1;
        hedef++;
        kaynak1++;
    }
    while(*kaynak2 != '\0'){
        *hedef = *kaynak2;
        hedef++;
        kaynak2++;
    }
    *hedef='\0';
    return p;
}
int main() {
    char a[]="birinci string... ";
    char b[]="ikinci string...";
    char c[35];
    
    printf("%s", str_birlestir(a,b,c));
    
	return 0;
}
```
    birinci string... ikinci string...
