```C
#include <stdio.h>

int main() {
    
    int a=45;
    printf("sayi: %d\n",a);
    printf("sayi: %x\n",a);
    printf("sayi: %X\n",a);
    printf("sayi: %o\n",a);
    
    a=0xa5e;
    printf("sayi: %d\n",a);
    printf("sayi: %x\n",a);
    printf("sayi: %X\n",a);
    printf("sayi: %o\n",a);
    
    a=057;
    printf("sayi: %d\n",a);
    printf("sayi: %x\n",a);
    printf("sayi: %X\n",a);
    printf("sayi: %o\n",a);
    
	return 0;
}
```

    sayi: 45
    sayi: 2d
    sayi: 2D
    sayi: 55
    sayi: 2654
    sayi: a5e
    sayi: A5E
    sayi: 5136
    sayi: 47
    sayi: 2f
    sayi: 2F
    sayi: 57



```C
#include <stdio.h>

int main() {
    
    int a=10;
    int b=12;
    printf("VE:    %X\n", a&b);
    printf("VEYA:  %X\n", a|b);
    printf("XOR:   %X\n", a^b);
    printf("DEĞ A: %X\n", ~a);
    
	return 0;
}
```

    VE:    8
    VEYA:  E
    XOR:   6
    DEĞ A: FFFFFFF5



```C
#include <stdio.h>

int main() {
    
    int a=10;
    
    printf("DEĞ A: %X\n", ~a);
    printf("DEĞ A: %d\n", ~a);
    printf("DEĞ A: %u\n", ~a);
     
	return 0;
}
```

    DEĞ A: FFFFFFF5
    DEĞ A: -11
    DEĞ A: 4294967285



```C
#include <stdio.h>

int main() {
    
    int a=13;
    
    printf("a << 1: %d\n", a<<1);
    printf("a << 2: %d\n", a<<2);
    printf("a >> 1: %d\n", a>>1);
    printf("a >> 2: %d\n", a>>2);
    
	return 0;
}
```

    a << 1: 26
    a << 2: 52
    a >> 1: 6
    a >> 2: 3



```C
#include <stdio.h>

int main() {
    int a=158, b;
    b=a | 1<<5;
    printf("%d, %X",b,b);
    
	return 0;
}
```

    190, BE


```C
#include <stdio.h>

int main() {
    int a=158, b;
    b=a & ~(1<<4);
    printf("%d, %X",b,b);
      
	return 0;
}
```

    142, 8E


```C
#include <stdio.h>

int main() {
    int a=158;
    if ((a & 1<<4)>0)
        printf("a sayisinin 4. biti 1 dir.");
    else
        printf("a sayisinin 4. biti 0 dir.");
    
	return 0;
}
```

    a sayisinin 4. biti 1 dir.


```C
#include <stdio.h>

int main() {
    int a=158;
    if ((a & 1<<5)>0)
        printf("a sayisinin 5. biti 1 dir.");
    else
        printf("a sayisinin 5. biti 0 dir.");
    
	return 0;
}
```

    a sayisinin 5. biti 0 dir.


```C
#include <stdio.h>

int main() {
    int a=158;
    int n=7;
    if ((a & 1<<n)>0)
        printf("a sayisinin %d. biti 1 dir.",n);
    else
        printf("a sayisinin %d. biti 0 dir.",n);
    
	return 0;
}
```

    a sayisinin 7. biti 1 dir.


```C
#include <stdio.h>

int main() {
    int a=158;
    int n=7;
    for(n=7;n>=0;n--){
        if ((a & 1<<n)>0)
            printf("1");
        else
            printf("0");
    }

	return 0;
}
```

    10011110
