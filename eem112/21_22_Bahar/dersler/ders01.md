**Değişken türleri**   
**tamsayi**
- int , short, char, long
- unsigned

**ondalikli sayi**
- float, double

**aritmetik operatörler:** + - * / %

**karşılaştırma operatöreri**
< > <= >= == !=  !



```C
#include <stdio.h>
int main() {
    printf("%d \n",3>2);

    printf("%d \n",3>2>1);
	return 0;
}
```

**if - else**

```C
#include <stdio.h>
int main() {
    int a=1, b=1;
    if(a>b)
        printf("birinci sayi ikinci sayidan buyuktur.");
    else if(a==b)
        printf("birinci sayi  ve ikinci sayi esittir.");
    else
        printf("ikinci sayi birinci sayidan buyuktur.");
	return 0;
}
```

**Döngüler**

```C
#include <stdio.h>
int main() {
	int i=0;
	
	while(i<10){
		printf("%d ",i);
		i=i+1;
	}
	
	printf("\n");
	
	i=0;
	while(i<10){
		printf("%d ",i);
		i += 1;
	}
	
	printf("\n");
	
	i=0;
	while(i<10){
		printf("%d ",i);
		i++;
	}
	
	printf("\n");
	
	i=0;
	while(i<10)
		printf("%d ",i++);
		
	printf("\n");
	
	i=0;
	while(i<10)
		printf("%d ",++i);
	
	printf("\n");
	
	for(i=0; i<10; i++)
		printf("%d ",i);
	
	printf("\n");
	
	for(i=0; i<10; ++i)
		printf("%d ",i);
		
	printf("\n");
	
	i=0;
	for( ; i<10; )
		printf("%d ",i++);
		
	printf("\n");
	
	i=0;
	for( ; ; ){
		printf("%d ",i++);
		if (i == 10)
			break;
	}
	
	printf("\n");
	
	for(i=0; i<10; ++i){
		if (i%2 == 0)
			continue;
		printf("%d ",i);
	}
	return 0;
}
```
    
**diziler**

```C
#include <stdio.h>
int main() {
    int a[10],i;
	for(i=0;i<10;i++)
		a[i]=i+10;
	
	for(i=0;i<10;i++)
		printf("%d:%d ",i, a[i]);	
	
	printf("%d ", a[5]);

	for(i=9;i>=0;i--)
		printf("%d:%d ",i, a[i]);
	return 0;
}
```
```C
#include <stdio.h>
int main() {
	int a[10]={1,2,3};
	int i;
	
	for(i=0;i<10;i++)
		printf("%d ",a[i]);
			
	printf("\n")	;
	printf("%d \n",a);
	printf("%d\n",&a[0]);
	printf("%d\n",&a[1]);
	printf("%d\n",&a[9]);
	return 0;
}
```

**cok boyutlu diziler**

```C
#include <stdio.h>
int main() {
    int a[10][10], b[10][10], c[10][10];
	int i, j;
	
	for(i=0;i<10;i++)
		for(j=0;j<10;j++)
			scanf("%d", &a[i][j]);
	
	for(i=0;i<10;i++)
		for(j=0;j<10;j++)
			scanf("%d", &b[i][j]);
			
	for(i=0;i<10;i++)
		for(j=0;j<10;j++)
			c[i][j]=a[i][j]+b[i][j];
			
	for(i=0;i<10;i++){
		for(j=0;j<10;j++)
			printf("%4.d ", c[i][j]);
		printf("\n");
	}
	return 0;
}
```
**fonksiyonlar**

```C
#include <stdio.h>
void topla(int a, int b){
	int c;
	c=a+b;
	printf("toplam: %d",c);
}
int main() {
	int x=10, y=20, z;
	topla(x,y);
	return 0;
}

```

```C
#include <stdio.h>
int topla(int a, int b){
	int c;
	c=a+b;
	return c;	
}
int main() {
	int x=10, y=20, z;
	z=topla(x,y);
	printf("toplam: %d",z);
	return 0;
}

```






```C
#include <stdio.h>
void klavyeden_dizi_oku(int x[], int n){
	int i;
	for(i=0;i<n;i++)
		scanf("%d",&x[i]);
}
void dizi_yazdir(int dizi[], int boyut){
	int i;
	for(i=0;i<boyut;i++)
	printf("%d ", dizi[i]);
	
}
int main() {
	int a[10]={1,2,3};
	int i;
	
	for(i=0;i<10;i++)
		printf("%d ",a[i]);
		
	klavyeden_dizi_oku(a,10);
	
	printf("\n");
	for(i=0;i<10;i++)
		printf("%d ",a[i]);	
	
	printf("\n");
	dizi_yazdir(a,7);	
	return 0;
}
```