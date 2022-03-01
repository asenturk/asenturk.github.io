```C
#include <stdio.h>
int main() {
	
	char a[]="bu bir stringdir.";
	printf("%c:%d",a[5],a[5]);
	
	return 0;
}
```



```C
#include <stdio.h>
#include <string.h>
int main() {
	
	char a[]="bu bir stringdir.";
	int i=0;
	printf("%c:%d\n",a[5],a[5]);
	printf("%d\n",strlen(a) );
	printf("%d\n",sizeof(a[0]));
	printf("%d\n",sizeof(a));
	//dizinin son elemani '\0' karakteridir.
	printf(" a dizisi: %s\n",a);
	
	for(i=0;a[i]!='\0';i++);
	printf("i:%d",i);
	
	return 0;
}
```




```C
#include <stdio.h>
void ters_cevir(char kaynak[], char hedef[]){
	int i,j;
	for(i=0; kaynak[i]!='\0';i++);
	
	for(j=i-1; j>=0; j--)
		hedef[i-1-j] = kaynak[j];
	
	hedef[i]='\0';
}
int main() {
	
	char a[]="bu bir stringdir.";
	char a_ters[50];
	
	ters_cevir(a, a_ters);
	printf("stringin tersi: %s",a_ters);
	
	return 0;
}
```