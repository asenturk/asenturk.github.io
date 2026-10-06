# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 5 - Python Programlama


### Klavyeden veri girmek


```python
a=input("bir deger giriniz")
b=input("ikinci degeri giriniz")
c=a+b
print("girilen iki degerin toplami:",c);
```

<pre>
    bir deger giriniz 10
    ikinci degeri giriniz 20
    

    girilen iki degerin toplami: 1020
</pre>
    


```python
a=input("bir deger giriniz")
b=input("ikinci degeri giriniz")
c=int(a)+int(b)
print("girilen iki degerin toplami:",c);
```

<pre>
    bir deger giriniz 10
    ikinci degeri giriniz 20
    

    girilen iki degerin toplami: 30
</pre>
    

- girilen bir metindeki boşluk sayısını bulan program:


```python
a=input("bir metin giriniz:")
bosluk_sayisi=a.count(" ")
print(f"girilen metinde {bosluk_sayisi} boşluk vardır.")
```

<pre>
    bir metin giriniz: ab    ada 4 4 4   1
    

    girilen metinde 10 boşluk vardır.
</pre>
    


```python
import math

print("bil silindirin hacmini hesaplayan program için")
r=float(input("yarıçapı giriniz:"))
h=float(input("yüksekliği giriniz:"))
hacim = math.pi*r**2*h
print(f"yaricapi {r} ve yüksekliği {h} olan silindirin hacmi: {hacim:.2f}")

```

<pre>
    bil silindirin hacmini hesaplayan program için
    

    yarıçapı giriniz: 3.5
    yüksekliği giriniz: 10.2
    

    yaricapi 3.5 ve yüksekliği 10.2 olan silindirin hacmi: 392.54
</pre>
    

### Boolean türü


```python
True, type(False)
```




<pre>
    (True, bool)
</pre>




```python
a=1
b=2
a>b, a<b, a>=b, a<=b, a==b, a!=b
```




<pre>
    (False, True, False, True, False, True)
</pre>




```python
a=1
b=1
a>b, a<b, a>=b, a<=b, a==b, a!=b
```




<pre>
    (False, False, True, True, True, False)
</pre>




```python
a="abc"
b="def"
a==b, a!=b, a>b
```




<pre>
    (False, True, False)
</pre>




```python
a="abc"
b="ABC"
a>b
```




<pre>
    True
</pre>




```python
"abc" in "defghiabcdef"
```




<pre>
    True
</pre>



### if-else-elif


```python
a=int(input("bir sayi giriniz:"))
if a>0:
    print("girilen sayi pozitiftir.")
```

<pre>
    bir sayi giriniz: 0
</pre>
    


```python
a=int(input("bir sayi giriniz:"))
if a>0:
    print("girilen sayi pozitiftir.")
else:
    print("girilen sayı 0 veya negatiftir")
```

<pre>
    bir sayi giriniz: -8
    

    girilen sayı 0 veya negatiftir
</pre>
    


```python
a=int(input("bir sayi giriniz:"))
if a>0:
    print("girilen sayi pozitiftir.")
elif a==0:
    print("girilen sayı 0'dır.")
else:
    print("girilen sayı negatiftir")
```

### Mantık operatörleri


```python
True and True, True and False
```




<pre>
    (True, False)
</pre>




```python
True or True, True or False, False or False
```




<pre>
    (True, True, False)
</pre>




```python
not True, not (True or False)
```




<pre>
    (False, False)
</pre>





### Listeler


```python
a=[5,1,2,3,9,5,2,6,10]
a
```




<pre>
    [5, 1, 2, 3, 9, 5, 2, 6, 10]
</pre>




```python
type(a)
```




<pre>
    list
</pre>




```python
len(a)
```




<pre>
    9
</pre>




```python
a[0],a[3],a[len(a)-1], a[-1], a[-3]
```




<pre>
    (5, 3, 10, 10, 2)
</pre>




```python
a[3:6], a[0:4],a[:4],a[4:]
```




<pre>
    ([3, 9, 5], [5, 1, 2, 3], [5, 1, 2, 3], [9, 5, 2, 6, 10])
</pre>




```python
a
```




<pre>
    [5, 1, 2, 3, 9, 5, 2, 6, 10]
</pre>




```python
a[1:7:2], a[::-1]
```




<pre>
    ([1, 3, 5], [10, 6, 2, 5, 9, 3, 2, 1, 5])
</pre>




```python
dir(a)
```



<pre>
    ['__add__',
     '__class__',
     '__contains__',
     '__delattr__',
     '__delitem__',
     '__dir__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__gt__',
     '__hash__',
     '__iadd__',
     '__imul__',
     '__init__',
     '__init_subclass__',
     '__iter__',
     '__le__',
     '__len__',
     '__lt__',
     '__mul__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__reversed__',
     '__rmul__',
     '__setattr__',
     '__setitem__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     'append',
     'clear',
     'copy',
     'count',
     'extend',
     'index',
     'insert',
     'pop',
     'remove',
     'reverse',
     'sort']
</pre>


```python
a
```




<pre>
    [5, 1, 2, 3, 9, 5, 2, 6, 10]
</pre>




```python
a.append(50)
a
```




<pre>
    [5, 1, 2, 3, 9, 5, 2, 6, 10, 50]
</pre>




```python
a.insert(0,10)
a
```




<pre>
    [10, 5, 1, 2, 3, 9, 5, 2, 6, 10, 50]
</pre>




```python
a.append("abc")
a
```




<pre>
    [10, 5, 1, 2, 3, 9, 5, 2, 6, 10, 50, 'abc']
</pre>




```python
a.remove(2)
a
```




<pre>
    [10, 5, 1, 3, 9, 5, 2, 6, 10, 50, 'abc']
</pre>




```python
del a[3]
a
```




<pre>
    [10, 5, 1, 9, 5, 2, 6, 10, 50, 'abc']
</pre>




```python
a.reverse()
a
```




<pre>
    ['abc', 50, 10, 6, 2, 5, 9, 1, 5, 10]
</pre>




```python
del a[0]
```


```python
a.sort()
a
```




<pre>
    [1, 2, 5, 5, 6, 9, 10, 10, 50]
</pre>




```python
a.sort(reverse=True)
a
```




<pre>
    [50, 10, 10, 9, 6, 5, 5, 2, 1]
</pre>




```python
len(a), sum(a), max(a), min(a)
```




<pre>
    (9, 98, 50, 1)
</pre>



```python
liste=["muz","elma","armut","karpuz","kiraz"]
len(liste)
```




<pre>
5
</pre>




```python
liste.sort()
liste
```




<pre>
    ['armut', 'elma', 'karpuz', 'kiraz', 'muz']
</pre>




```python
liste.sort(reverse=True)
liste
```




<pre>
    ['muz', 'kiraz', 'karpuz', 'elma', 'armut']
</pre>




```python
liste[-1]="Armut"
liste[2]="Karpuz"
liste
```




<pre>
    ['muz', 'kiraz', 'Karpuz', 'elma', 'Armut']
</pre>




```python
liste.sort()
liste
```




<pre>
    ['Armut', 'Karpuz', 'elma', 'kiraz', 'muz']
</pre>




```python
liste.sort(key=str.lower)
liste
```




<pre>
    ['Armut', 'elma', 'Karpuz', 'kiraz', 'muz']
</pre>


### Döngüler


```python
i=0
while i<10:
    print(i, end=" ")
    i += 1
```

<pre>
    0 1 2 3 4 5 6 7 8 9 
</pre>

### range fonksiyonu


```python
list(range(10))
```




<pre>
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
</pre>




```python
list(range(10,20))
```




<pre>
    [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
</pre>




```python
list(range(10,20,3))
```




<pre>
    [10, 13, 16, 19]
</pre>




```python
for i in range(10):
    print(i, end=" ")
```

<pre>
    0 1 2 3 4 5 6 7 8 9 
</pre>


```python
for i in range(10,50,7):
    print(i**2, end=" ")
```

<pre>
    100 289 576 961 1444 2025
</pre> 


```python
for i in range(10,50):
    if i%7==0:
        print(i,i**3)
```

<pre>
    14 2744
    21 9261
    28 21952
    35 42875
    42 74088
    49 117649
</pre>
    


```python
for i in range(10,25):
    if i%7==0 or i%3==0:
        print(i,i**3)
```

<pre>
    12 1728
    14 2744
    15 3375
    18 5832
    21 9261
    24 13824
</pre>
    


```python
a=[]
for i in range(10,25):
    if i%7==0 or i%3==0:
        a.append(i)
```


```python
a, a[-1],a[2]
```




<pre>
    ([12, 14, 15, 18, 21, 24], 24, 15)
</pre>




```python
bolumler=["bilgisayar","elektrik","mekatronik","makine","insaat"]
for bolum in bolumler:
    print(bolum)
```

<pre>
    bilgisayar
    elektrik
    mekatronik
    makine
    insaat
</pre>
    


```python
metin="bu bir yazıdır."
for karakter in metin:
    print(karakter,end="-")
```

<pre>
    b-u- -b-i-r- -y-a-z-ı-d-ı-r-.-
</pre>
