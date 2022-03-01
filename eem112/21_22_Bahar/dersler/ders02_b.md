```C
#include <stdio.h>
int main() {
	
	int a=10, b=20;
	printf("a:%d, b:%d \n",a,b);
	printf("a:%x, b:%x \n",a,b);
	printf("a:%d, b:%d \n",&a, &b);
	printf("a:%u, b:%u \n",&a, &b);
	printf("a:%x, b:%x \n",&a, &b);

	return 0;
}
```

```C
#include <stdio.h>
int main() {
	
	char a[5];
	short b[5];
	int c[5];
	
	printf("a: %d\n",a);
	printf("&a[0]: %d\n",&a[0]);
	printf("&a[3]: %d\n",&a[3]);
	
	printf("b: %d\n",b);
	printf("&b[0]: %d\n",&b[0]);
	printf("&b[3]: %d\n",&b[3]);
	
	printf("c: %d\n",c);
	printf("&c[0]: %d\n",&c[0]);
	printf("&c[3]: %d\n",&c[3]);

	return 0;
}
```

```C
#include <stdio.h>
int main() {
	
	int a=10, b=20;
	int *p;
	
	p = &a;
	printf("%d\n", *p);
	*p = *p + 5;
	printf("%d\n", *p);
	printf("%d\n", a);
	
	p = &b;
	printf("%d\n", *p);
	*p = *p + 5;
	printf("%d\n", *p);
	printf("%d\n", b);
	printf("%d\n", a);

	return 0;
}
```

```C
#include <stdio.h>
int main() {
	
	int a=10;
	int *p, *q;
	
	p=&a;
	
	q=&a;
	q=p;
	printf("%d\n", *p);
	printf("%d\n", *q);
	
	(*p)++;
	printf("%d\n", *p);
	printf("%d\n", a);
	
	*q += 2;
	printf("%d\n", *q);
	printf("%d\n", a);

	return 0;
}
```


```C
#include <stdio.h>
void topla(float *sayi1, float *sayi2, float *toplam){
	*toplam = *sayi1 + *sayi2;
}
int main() {
	
	float a=10, b=20, c;
	topla(&a, &b, &c);
	printf("%f\n", c);

	return 0;
}
```




```C
#include <stdio.h>
int main() {
	
	int a[10]={5,7,9,11,13};
	int *isaretci;
	
	//isaretci=&a[0];
	isaretci = a;
	
	printf("%d\n",a[0]);
	*isaretci = *isaretci + 5;
	printf("%d\n",a[0]);
	(*isaretci)++;
	printf("%d\n",a[0]);
	
	printf("%d\n",isaretci);
	isaretci++;
	printf("%d\n",isaretci);
	printf("%d\n",*isaretci);

	return 0;
}
```

```C
#include <stdio.h>
int main() {
	
	int a[10]={5,7,9,11,13};
	int *isaretci;

	for(isaretci=a; isaretci <= &a[4]   ;isaretci++)
		printf("%d ", *isaretci);

	return 0;
}
```