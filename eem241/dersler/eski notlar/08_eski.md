# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 8 - Python Programlama




### tuple (demet)


```python
a=[1,2,3]
type(a)
```

<pre>
    list
</pre>


```python
b=(1,2,3)
type(b)
```

<pre>
    tuple
</pre>



```python
len(b)
```

<pre>
   3
</pre>




```python
b[0]=5
# bu kod hata verir. Çünkü demet türüne atama yapılamaz.
```


```python
a=(3,4,5,6,7,8,9,10)
len(a)
```

<pre>
    8
</pre>


```python
a[0], a[1], a[2:5],a[-1], a[:3], a[:-3:-1], a[::2]
```

<pre>
    (3, 4, (5, 6, 7), 10, (3, 4, 5), (10, 9), (3, 5, 7, 9))
</pre>


```python
min(a), max(a), sum(a), len(a)
```


<pre>
    (3, 10, 52, 8)
</pre>


```python
a=(1,5,"abc",3,True,(8,9),[1,2,3])
a
```


<pre>
    (1, 5, 'abc', 3, True, (8, 9), [1, 2, 3])
</pre>


```python
for i in a:
    print(f"{i}: {type(i)}")
```

<pre>
    1: <class 'int'>
    5: <class 'int'>
    abc: <class 'str'>
    3: <class 'int'>
    True: <class 'bool'>
    (8, 9): <class 'tuple'>
    [1, 2, 3]: <class 'list'>
</pre>
    


```python
toplam=0
for i in a:
    if type(i)==int:
        toplam += i
print("tuple icindeki tamsayıların toplamı:", toplam)
```

<pre>
    tuple icindeki tamsayıların toplamı: 9
</pre>





- in kullanımı

```python
metin="abc"
"a" in metin
```

<pre>
    True
</pre>

```python
liste=[1,2,3,4,5]
3 in liste
```

<pre>
    True
</pre>




```python
tpl=(1,2,3,4,5)
3 in liste
```


<pre>
    True
</pre>


```python
tpl=(1,2,3,4,5)
3 not in liste
```

<pre>
    False
</pre>




```python
a=(1,2,"metin",5.0,True, [1,2,3],"abc","xyzwq",1,"def")
for eleman in a:
    if type(eleman)==str and "e" in eleman:
        print(eleman)
```

<pre>
    metin
    def
</pre>
    


```python
# a tuple ının 7. elemanının son harfine nasıl ulaşırım.
a[7][-1]
```




<pre>
    'q'
</pre>



### tuple tanımlama ve tuple elemanlarını atama

```python
1,2
```




<pre>
    (1, 2)
</pre>




```python
a,b=1,2
```


```python
a
```




<pre>
    1
</pre>




```python
b
```




<pre>
    2
</pre>




```python
a,b=(1,2)
a
```




<pre>
    1
</pre>




```python
a,b=(1,2,3)
# bu kod hata verir.
```


```python
a,*b=(1,2,3)
a,b
```


<pre>
    (1, [2, 3])
</pre>




```python
a,b,c,*d=1,2,3,4,5,6,7,8,9,10
d
```




<pre>
    [4, 5, 6, 7, 8, 9, 10]
</pre>




```python
a,*b,c,d=1,2,3,4,5,6,7,8,9,10
b
```




<pre>
    [2, 3, 4, 5, 6, 7, 8]
</pre>




```python
a=1
a
```

<pre>
    1
</pre>


```python
a=1,
a
```


<pre>
    (1,)
</pre>

```python
a=1,2,3,4,5,6,3,8,9,10
```


```python
a.count(3)
```


<pre>
    2
</pre>


```python
a.index(5)
```


<pre>
    4
</pre>




```python
a
```


<pre>
    (1, 2, 3, 4, 5, 6, 3, 8, 9, 10)
</pre>




```python
b=tuple(i for i in a if i%2==1)
b
```




<pre>
    (1, 3, 5, 3, 9)
</pre>




### set (küme)


```python
a=[1,2]
type(a)
```


<pre>
    list
</pre>




```python
a=(1,2)
type(a)
```




<pre>
    tuple
</pre>




```python
a={1,2}
type(a)
```




<pre>
    set
</pre>




```python
a={1,2,3,3,3,3,1,2,3,4}
a
```




<pre>
    {1, 2, 3, 4}
</pre>




```python
a=[1,2,2,3,3,1,2,5]
a
```




<pre>
    [1, 2, 2, 3, 3, 1, 2, 5]
</pre>




```python
a=list(set(a))
a
```




<pre>
    [1, 2, 3, 5]
</pre>




```python
a={1,2,3,4,5,6}
b={4,5,6,7,8,9}
```


```python
a.intersection(b)
```




<pre>
    {4, 5, 6}
</pre>




```python
a.union(b)
```




<pre>
    {1, 2, 3, 4, 5, 6, 7, 8, 9}
</pre>




```python
a-b
```




<pre>
    {1, 2, 3}
</pre>




```python
a.difference(b)
```




<pre>
    {1, 2, 3}
</pre>




```python
b-a
```




<pre>
    {7, 8, 9}
</pre>




```python
a.symmetric_difference(b)
```




<pre>
    {1, 2, 3, 7, 8, 9}
</pre>


```python
{i for i in range(2,15,3)}
```




<pre>
    {2, 5, 8, 11, 14}
</pre>




```python
a=set()
a.add(1)
a.add(2)
a.add(1)
```



```python
a={"a",1,1.0,2,7,"abc",1}
a
```


<pre>
    {1, 2, 7, 'a', 'abc'}
</pre>


```python
a[0]
# hata verir, küme indekslenebilir değildir.
```



### Dictionary (Sözlük)


- sozlukte {anahtar:deger} seklinde veriler olur



```python
a={"isim":"ali", "numara":123, "bolum":"eem"}
a
```




<pre>
    {'isim': 'ali', 'numara': 123, 'bolum': 'eem
</pre>'}




```python
a["bolum"],a["isim"]
```




<pre>
    ('eem', 'ali')
</pre>




```python
a[0]
# 0. anahtar sözlükte tanımlı olmadığından hata verir.
```





```python
a={"isim":"ali", "numara":123, "bolum":"eem",1:100}
a
```




<pre>
    {'isim': 'ali', 'numara': 123, 'bolum': 'eem', 1: 100
</pre>}




```python
a[1]
```




<pre>
    100
</pre>




```python
a["ders"]="Programlama"
```


```python
a["not"]=55
a
```




<pre>
  {'isim': 'ali',
     'numara': 123,
     'bolum': 'eem',
     1: 100,
     'ders': 'Programlama',
     'not': 55}
</pre>




```python
a[0]=500
a
```




<pre>
    {'isim': 'ali',
     'numara': 123,
     'bolum': 'eem',
     1: 100,
     'ders': 'Programlama',
     'not': 55,
     0: 500}
</pre>




```python
# a sozluğündeki eem'nin ortadaki harfine ulaşmak için:
a["bolum"][1]
```




<pre>
    'e'
</pre>




```python
a.values()
```




<pre>
    dict_values(['ali', 123, 'eem', 100, 'Programlama', 55, 500])
</pre>




```python
a.keys()
```




<pre>
    dict_keys(['isim', 'numara', 'bolum', 1, 'ders', 'not', 0
</pre>])




```python
list(a.keys())[2][-1]
```




<pre>
    'm'
</pre>




```python
a.items()
```




<pre>
    dict_items([('isim', 'ali'), ('numara', 123), ('bolum', 'eem'), (1, 100), ('ders', 'Programlama'), ('not', 55), (0, 500)])
</pre>




```python
x,y=(1,2)
y
```




<pre>
    2
</pre>




```python
for key,value in a.items():
    print(f"{key}: {value}")
```

<pre>
    isim: ali
    numara: 123
    bolum: eem
    1: 100
    ders: Programlama
    not: 55
    0: 500
</pre>
    


```python
for x in a:
    print(x)
```

<pre>
    isim
    numara
    bolum
    1
    ders
    not
    0
</pre>
    


```python
for x in a:
    print(a[x])
```

<pre>
    ali
    123
    eem
    100
    Programlama
    55
    500
</pre>
    


```python
aile={
    "baba":{"isim":"ali", "yas":40, "meslek":"öğretmen"},
    "anne":{"isim":"ayşe","yas":35,"meslek":"memur"},
    "cocuk":{"isim":"mehmet","yas":10}
}
aile
```




<pre>
    {'baba': {'isim': 'ali', 'yas': 40, 'meslek': 'öğretmen'},
     'anne': {'isim': 'ayşe', 'yas': 35, 'meslek': 'memur'},
     'cocuk': {'isim': 'mehmet', 'yas': 10}}
</pre>




```python
aile["cocuk"]["isim"]
```




<pre>
    'mehmet'
</pre>




```python
aile["cocuk"]["meslek"]="Öğrenci"
aile
```




<pre>
    {'baba': {'isim': 'ali', 'yas': 40, 'meslek': 'öğretmen'},
     'anne': {'isim': 'ayşe', 'yas': 35, 'meslek': 'memur'},
     'cocuk': {'isim': 'mehmet', 'yas': 10, 'meslek': 'Öğrenci'}}
</pre>




```python
for kisi in aile:
    print(aile[kisi]["isim"])
```

<pre>
    ali
    ayşe
    mehmet
</pre>
    


```python
for bilgi in aile.values():
    print(bilgi["isim"])
```

<pre>
    ali
    ayşe
    mehmet
</pre>
    


```python
x={1,2,3}
type(x)
```




<pre>
    set
</pre>




```python
x={1:2}
type(x)
```




<pre>
    dict
</pre>




```python
x=set()
```


```python
# sayılar ve kareleri
sayilar_ve_kareleri = {}
for i in range(1,10):
    sayilar_ve_kareleri[i]=i**2

sayilar_ve_kareleri
```




<pre>
    {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
</pre>

```python
x={i:i*i for i in range(1,10)}
x
```

<pre>
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
</pre>



```python
metin="abcdeabddfaaabcbdbddeebdac"

harf_sayilari = dict() # {} yapabilirdik

for harf in metin:
    if harf not in harf_sayilari:
        harf_sayilari[harf]=1
    else:
        harf_sayilari[harf] += 1
harf_sayilari
```




<pre>
    {'a': 6, 'b': 6, 'c': 3, 'd': 7, 'e': 3, 'f': 1}
</pre>




```python
for harf, sayi in harf_sayilari.items():
    print(f"{harf} harfinden {sayi} tane var")
```

<pre>
    a harfinden 6 tane var
    b harfinden 6 tane var
    c harfinden 3 tane var
    d harfinden 7 tane var
    e harfinden 3 tane var
    f harfinden 1 tane var
</pre>
    


```python
for harf in harf_sayilari:
    print(f"{harf} harfinden {harf_sayilari[harf]} tane var")
```

<pre>
    a harfinden 6 tane var
    b harfinden 6 tane var
    c harfinden 3 tane var
    d harfinden 7 tane var
    e harfinden 3 tane var
    f harfinden 1 tane var
</pre>
    



### Türlerin bool karşılıkları


```python
bool(1),bool(0),bool(-1),bool([0]),bool([]),bool(""),bool("0")
```



<pre>

    (True, False, True, True, False, False, True)
</pre>



### any all


```python
a=[True, True,False]
all(a), any(a)
```



<pre>
    (False, True)
</pre>




```python
a=[1,2,1,4,2,0,1,2,3]

all(a)
```



<pre>
    False
</pre>




```python
sifir_var=False
for sayi in a:
    if sayi==0:
        sifir_var=True
        break
sifir_var

```



<pre>
    True
</pre>



```python
if all(a):
    print("listenin icinde 0 yok")
else:
    print("listenin icinde 0 var")
```



<pre>
    True
</pre>



```python
a=[1,2,1,4,2,0,1,6,2,3]
if any([i>5 for i in x]):
    print("listede 5'ten büyük en az 1 sayı var")
```



<pre>
    [False, False, False, False, False, False, False, True, False, False]
</pre>


### enumerate


```python
a="bu bir metindir."
```


```python
i=0
for kar in a:
    print(f"{i}:{kar}", end=" ")
    i += 1
```
<pre>
    0:b 1:u 2:  3:b 4:i 5:r 6:  7:m 8:e 9:t 10:i 11:n 12:d 13:i 14:r 15:. 
</pre>

```python
for i, kar in enumerate(a):
    print(f"{i}:{kar}", end=" ")
```

    0:b 1:u 2:  3:b 4:i 5:r 6:  7:m 8:e 9:t 10:i 11:n 12:d 13:i 14:r 15:. 


```python
list(enumerate(a, start=1))
```



<pre>
     [(1, 'b'),
     (2, 'u'),
     (3, ' '),
     (4, 'b'),
     (5, 'i'),
     (6, 'r'),
     (7, ' '),
     (8, 'm'),
     (9, 'e'),
     (10, 't'),
     (11, 'i'),
     (12, 'n'),
     (13, 'd'),
     (14, 'i'),
     (15, 'r'),
     (16, '.')]
</pre>





```python
a=[1,4,3,2,1]
b=[3,2,2,3,4]
c=[]
```


```python
for i in range(len(a)):
    c.append(a[i]+b[i])
c
```



<pre>
    [4, 6, 5, 5, 5]
</pre>



```python
i=0
c=[]
for sayi in a:
    c.append(sayi+b[i])
    i+=1
c
```



<pre>
    [4, 6, 5, 5, 5]
</pre>



```python
c=[]
for i, sayi in enumerate(a):
    c.append(sayi+b[i]) 
c
```



<pre>
    [4, 6, 5, 5, 5]
</pre>


### zip fonksiyonu


```python
c=[]
for i,j in zip(a,b):
    c.append(i+j) 
c
```



<pre>
    [4, 6, 5, 5, 5]
</pre>



```python
[i+j for i,j in zip(a,b)]
```


```python
print(a)
print(b)
```

<pre>
    [1, 4, 3, 2, 1]
    [3, 2, 2, 3, 4]
</pre>	
    


```python
list(zip(a,b))
```



<pre>
    [(1, 3), (4, 2), (3, 2), (2, 3), (1, 4)]
</pre>




```python
#a ve b listesinin elemanlarını kullanarak bir sozluk yapalım
```


```python
a=[1, 4, 3, 2, 7]
b=[3, 2, 2, 3, 4]
```


```python
c=dict()
for i,j in zip(a,b):
    c[i]=j
c
```



<pre>
    {1: 3, 4: 2, 3: 2, 2: 3, 7: 4}
</pre>



```python
{i:j for i,j in zip(a,b)}
```



<pre>
    {1: 3, 4: 2, 3: 2, 2: 3, 7: 4}
</pre>



```python
{x[0]:x[1] for x in zip(a,b)}
```



<pre>
    {1: 3, 4: 2, 3: 2, 2: 3, 7: 4}
</pre>



```python
kisiler=["mehmet","ali","ahmet","ayşe"]
sehirler = ["isparta","burdur","antalya","denizli"]
```


```python
i=0
for i in range(len(kisiler)):
    print(f"{kisiler[i]}: {sehirler[i]}")
```

<pre>
    mehmet: isparta
    ali: burdur
    ahmet: antalya
    ayşe: denizli
</pre>	
    


```python
for i, kisi in enumerate(kisiler):
    print(f"{kisi}: {sehirler[i]}")
```

<pre>
    mehmet: isparta
    ali: burdur
    ahmet: antalya
    ayşe: denizli
</pre>	
    


```python
for kisi, sehir in zip(kisiler,sehirler):
    print(f"{kisi}: {sehir}")
```

<pre>
    mehmet: isparta
    ali: burdur
    ahmet: antalya
    ayşe: denizli
</pre>	
    

### kutuphanelerden fonksiyon kullanma


```python
import math

dir(math)
# bu komut ile matematik kütüphanesindeki fonksiyonlar listelenir.
```

 

```python
help(math.sin)
```

<pre>
    Help on built-in function sin in module math:
    sin(x, /)
        Return the sine of x (measured in radians).
</pre>

```python
math.e, math.pi
```



<pre>
    (2.718281828459045, 3.141592653589793)
</pre>



```python
math.sqrt(16)
```



<pre>
    4.0
</pre>



```python
from math import pi
```


```python
pi
```



<pre>
    3.141592653589793
</pre>



```python
import math as matematik
```


```python
matematik.pi
```



<pre>
    3.141592653589793
</pre>



```python
from math import pi as pi_sayisi
```


```python
pi_sayisi
```



<pre>
    3.141592653589793
</pre>



```python
from math import pi as pi_sayisi, e as e_sayisi
```


```python
from math import sin, pi, radians
```


```python
for derece in range(0,360,30):
    # derece_rad = (derece/180)*pi
    derece_rad = radians(derece)

    print(f"{derece:3} : {sin(derece_rad):.2f}")
```

<pre>
      0 : 0.00
     30 : 0.50
     60 : 0.87
     90 : 1.00
    120 : 0.87
    150 : 0.50
    180 : 0.00
    210 : -0.50
    240 : -0.87
    270 : -1.00
    300 : -0.87
    330 : -0.50
</pre>	
    




```python
from math import gcd as ebob
```


```python
ebob(21,14)
```

<pre>
    7
</pre>

```python
import math
```

```python
math.factorial(100)
```

<pre>
    93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000
</pre>	