# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 9 - Python Programlama




### fonksiyonlar


```python
def topla(a,b,c):
    return a+b+c
topla(1,2,3)
```



<pre>
    6
</pre>



```python
def topla(a,b,c):
    toplam = a+b+c
    return toplam
topla(1,2,3)
```



<pre>
    6
</pre>



```python
def topla(a,b,c):
    parametreler = (a,b,c)
    toplam = 0
    for parametre in parametreler:
        if type(parametre)==int or type(parametre)==float:
            toplam += parametre
        else:
            print(f"{c} sayı değil")
    
    return toplam
topla(5,2,"3")
```

<pre>
    3 sayı değil
    




    7
</pre>	




```python
def topla(a,b,c):
    return a+b+c
topla(1,2)
```


<pre>
    ---------------------------------------------------------------------------
    

    TypeError                                 Traceback (most recent call last)
    

    D:\Temps\Temp\ipykernel_14060\336.py in <cell line: 3>()
    

          1 def topla(a,b,c):
    

          2     return a+b+c
    

    ----> 3 topla(1,2)
    

    
    

    TypeError: topla() missing 1 required positional argument: 'c'
</pre>	



```python
def topla(a,b=0,c=0):
    toplam = a+b+c
    return toplam
```


```python
topla(1)
```



<pre>
    1
</pre>



```python
def topla(a,b,*args):
    print(args)
```


```python
topla(1,2,9,2,3,4,5)
```
<pre>
    (9, 2, 3, 4, 5)
</pre>    


```python
def topla(a,b,*args):
    toplam = a+b

    for arg in args:
        toplam += arg

    return toplam
```


```python
topla(1,2,3,1,3,1,2,3,4,5,6,4,1)
```



<pre>
    36
</pre>



```python
import math
def uzaklik(a:tuple, b:tuple)->float:
    """ birinci parametre x1,y1 şeklinde bir noktanın koordinatları olmalı,
    ikinci parametre x2,y2 şeklinde bir noktanın koordinatları olmalı,
    fonksiyon girilen noktalar arasındaki uzaklığı döndürür.
    """
    x1,y1 = a
    x2,y2 = b
    uzaklik = math.sqrt((x1-x2)**2+(y1-y2)**2)
    return uzaklik

uzaklik((1,1),(4,5))

```



<pre>
    5.0
</pre>



```python
help(uzaklik)
```

<pre>
    Help on function uzaklik in module __main__:
    
    uzaklik(a: tuple, b: tuple) -> float
        birinci parametre x1,y1 şeklinde bir noktanın koordinatları olmalı,
        ikinci parametre x2,y2 şeklinde bir noktanın koordinatları olmalı,
        fonksiyon girilen noktalar arasındaki uzaklığı döndürür.
    
    

</pre>

### lambda


```python
a=lambda x: x+2
```


```python
a(2)
```



<pre>
    4
</pre>



```python
topla=lambda x,y:x+y
```


```python
topla(1,4)
```



<pre>
    5
</pre>



```python
tuple_topla = lambda x: x[0]+x[1]
a=(4,5)
tuple_topla(a)
```



<pre>
    9
</pre>



```python
a=[(3,2),(1,4),(5,1)]
a
```



<pre>
    [(3, 2), (1, 4), (5, 1)]
</pre>



```python
a.sort()
a
```



<pre>
    [(1, 4), (3, 2), (5, 1)]
</pre>



```python
a.sort(key=lambda x:x[1])
a
```



<pre>
    [(5, 1), (3, 2), (1, 4)]
</pre>


### karmaşık sayılar


```python
a=3+5j
type(a)
```

<pre>
    complex
</pre>


```python
b=5+7j
a+b
```

<pre>
    (8+12j)
</pre>


```python
dir(a)
```




<pre>
    ['__abs__',
     '__add__',
     '__bool__',
     '__class__',
     '__delattr__',
     '__dir__',
     '__divmod__',
     '__doc__',
     '__eq__',
     '__float__',
     '__floordiv__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getnewargs__',
     '__gt__',
     '__hash__',
     '__init__',
     '__init_subclass__',
     '__int__',
     '__le__',
     '__lt__',
     '__mod__',
     '__mul__',
     '__ne__',
     '__neg__',
     '__new__',
     '__pos__',
     '__pow__',
     '__radd__',
     '__rdivmod__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__rfloordiv__',
     '__rmod__',
     '__rmul__',
     '__rpow__',
     '__rsub__',
     '__rtruediv__',
     '__setattr__',
     '__sizeof__',
     '__str__',
     '__sub__',
     '__subclasshook__',
     '__truediv__',
     'conjugate',
     'imag',
     'real']
</pre>	 




```python
a.conjugate(),a.real, a.imag
```

<pre>
    ((3-5j), 3.0, 5.0)
</pre>


```python
a=3+4j
abs(a)
```

<pre>
    5.0
</pre>


```python
import cmath
```


```python
dir(cmath)
```




<pre>
    ['__doc__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     'acos',
     'acosh',
     'asin',
     'asinh',
     'atan',
     'atanh',
     'cos',
     'cosh',
     'e',
     'exp',
     'inf',
     'infj',
     'isclose',
     'isfinite',
     'isinf',
     'isnan',
     'log',
     'log10',
     'nan',
     'nanj',
     'phase',
     'pi',
     'polar',
     'rect',
     'sin',
     'sinh',
     'sqrt',
     'tan',
     'tanh',
     'tau']
</pre>	 




```python
a=3+4j
b=5+12j
```


```python
a+b,a-b,a*b,a/b
```



<pre>
    ((8+16j), (-2-8j), (-33+56j), (0.37278106508875736-0.09467455621301774j))
</pre>



```python
r=abs(a)
aci=cmath.phase(a)
aci_derece = (aci / cmath.pi)*180
r,aci_derece
```



<pre>
    (5.0, 53.13010235415597)
</pre>



```python
def kartezyene_cevir(kutupsal_kar_sayi):
    r, theta = kutupsal_kar_sayi
    theta_rad=(theta/180)*cmath.pi
    return cmath.rect(r, theta_rad)
```


```python
def kutupsala_cevir(z):
    r, theta= cmath.polar(z)
    theta_derece=(theta/cmath.pi)*180
    return (r, theta_derece)
```


```python
x=kutupsala_cevir(3+4j + kartezyene_cevir((5.0, 53.13010235415597)))
x
```



<pre>
    (10.0, 53.13010235415597)
</pre>




### local global değişkenler


```python
a=1
def f():
    print("f fonksiyonu:",a)
f()
print(a)
```

<pre>
    f fonksiyonu: 1
    1
</pre>
    


```python
a=1
def f():
    a=2
    print("f fonksiyonu:",a)
f()
print(a)
```

<pre>
    f fonksiyonu: 2
    1
</pre>
    


```python
a=1
def f():
    a = a+5
    print("f fonksiyonu:",a)
f()
print(a)
```


<pre>
    ---------------------------------------------------------------------------

    UnboundLocalError                         Traceback (most recent call last)

    Cell In[2], line 5
          3     a = a+5
          4     print("f fonksiyonu:",a)
    ----> 5 f()
          6 print(a)
    

    Cell In[2], line 3, in f()
          2 def f():
    ----> 3     a = a+5
          4     print("f fonksiyonu:",a)
    

    UnboundLocalError: cannot access local variable 'a' where it is not associated with a value
</pre>



```python
a=1
def f():
    global a
    a = a+5
    print("f fonksiyonu:",a)
f()
print(a)
```

<pre>
    f fonksiyonu: 6
    6
</pre>
    

### Dosya okuma, dosyaya yazma
- dosya okuma yazma modları: r, w, a
- bir üst klasöre geçmek için iki nokta ".." kullanılır.


```python
f=open("dosyalar/a.txt","r")
icerik=f.read()
f.close()
```


```python
print(icerik)
```

<pre>
    abc
    def
</pre>
    

Eğer python programı x klasöründe, text dosyası y klasöründe ise a.txt için dosya yolu: ../y/a.txt olur.


```python
f=open("a.txt","r", encoding="utf8")
icerik=f.read()
f.close()
```


```python
print(icerik)
```

<pre>
    abc
    def
</pre>
    


```python
metin="123,234,abc"
f=open("a.txt","w", encoding="utf8")
f.write(metin)
f.close()
```


```python
metin="123,234,abc"
f=open("a.txt","a", encoding="utf8")
f.write(metin)
f.close()
```



### Nesne Yönelimli Programlama


```python
class Kisi:
    def selam(self):
        print("Merhaba")
```


```python
mehmet = Kisi()
mehmet.selam()
```

<pre>
    Merhaba
</pre>
    


```python
class Kisi:
    def __init__(self, isim, yas):
        self.isim = isim
        self.yas = yas
    
    def bilgi(self):
        print(f"{self.isim} isimli kişinin yaşı: {self.yas}")

```


```python
ogrenci=Kisi("ali",22)
```


```python
ogrenci.yas, ogrenci.isim
```




<pre>
    (22, 'ali')
</pre>




```python
ogrenci.bilgi()
```

<pre>
    ali isimli kişinin yaşı: 22
</pre>
    



```python
class Ogrenci(Kisi):
    def __init__(self, isim, yas, sinif=None):
        super().__init__(isim, yas)
```


```python
ogrenci1 = Ogrenci("ali",22,4)
ogrenci1.bilgi()
```

<pre>
    ali isimli kişinin yaşı: 22
</pre>
    


```python
class Ogrenci(Kisi):
    def __init__(self, isim, yas, sinif):
        super().__init__(isim, yas)
        
        self.sinif=sinif
    
    def sinif_bilgisi(self):
        print(f"{self.isim} isimli ögrencinin sınıfı: {self.sinif} ")
```


```python
ogrenci1 = Ogrenci("ali",22,4)
ogrenci1.bilgi()
ogrenci1.sinif_bilgisi()
```

<pre>
    ali isimli kişinin yaşı: 22
    ali isimli ögrencinin sınıfı: 4
</pre> 
    


```python
import math

class Sekil:
    def cevre(self):
        return 0
    def  alan(self):
        return 0

class Dikdortgen(Sekil):
    def __init__(self, uzunluk, genislik):
        super().__init__()
        self.uzunluk  = uzunluk
        self.genislik = genislik
    
    def cevre(self):
        return 2*(self.uzunluk+self.genislik)
    
    def alan(self):
        return self.uzunluk*self.genislik
    
    def __str__(self):
        return f"{self.genislik}x{self.uzunluk} dikdortgen"
    
    def __repr__(self):
        return f"{self.genislik}x{self.uzunluk} dikdortgen"
    
    #less than
    def __lt__(self,other):
        return self.alan() < other.alan()

    
class Daire(Sekil):
    def __init__(self, yaricap):
        super().__init__()
        self.yaricap = yaricap
    
    def cevre(self):
        return 2*math.pi*self.yaricap
    
    def alan(self):
        return math.pi * self.yaricap**2
    
    def __str__(self):
        return f"{self.yaricap} yaricapinda daire"
    
    def __repr__(self):
        return f"{self.yaricap} yaricapinda daire"
    
    def __lt__(self,other):
        return self.alan() < other.alan()



```


```python
a=Dikdortgen(10,20)
a.cevre(),a.alan()
```




<pre>
    (60, 200)
</pre>




```python
print(a)
```

<pre>
    20x10 dikdortgen
</pre>
    


```python
a
```




<pre>
    20x10 dikdortgen
</pre>




```python
b=Daire(5)
b.alan()
```




<pre>
    78.53981633974483
</pre>




```python
b
```



<pre>
    5 yaricapinda daire
</pre>




```python
a>b
```




<pre>
    True
</pre>




```python
import cmath
class KarmasikSayi:
    def __init__(self, sayi):
        if type(sayi)==complex:
            self.sayi = sayi
        elif type(sayi)==tuple and len(sayi)==2:
            r, theta = sayi
            theta_rad = (theta/180)*cmath.pi
            self.sayi=cmath.rect(r, theta)
        else:
            print("sayı formatın hata var")
    
    def kutupsal(self):
        r, theta_rad=cmath.polar(self.sayi)
        theta = (theta_rad / cmath.pi)*180
        return r, theta
    
    def __str__(self):
        return f"{self.sayi.real} + j{self.sayi.imag}"
    
    def __repr__(self):
        return f"{self.sayi.real} + j{self.sayi.imag}"
    
    def __add__(self, other):
        toplam=self.sayi+other.sayi
        return KarmasikSayi(toplam)
    
    def __mul__(self, other):
        r1, theta1 = self.kutupsal()
        r2, theta2 = other.kutupsal()
        r=r1*r2
        theta=theta1+theta2
        return KarmasikSayi((r, theta))
    
    def __truediv__(self, other):
        r1, theta1 = self.kutupsal()
        r2, theta2 = other.kutupsal()
        r=r1/r2
        theta=theta1-theta2
        return KarmasikSayi((r, theta)) 
    
    def __abs__(self):
        return abs(self.sayi)
    
    def __lt__(self, other):
        return abs(self.sayi) < abs(other.sayi)

```


```python
a = KarmasikSayi(1+2j)
b = KarmasikSayi((5,53.13))
```


```python
print(a)
```

<pre>
    1.0 + j2.0
</pre>
    


```python
a+b
```




<pre>
    -3.809298179237886 + j3.3677174500528815
</pre>




```python
a*b
```




<pre>
    2.2841922595086497 + j10.94451761027414
</pre>




```python
a/b
```




<pre>
    0.44158298088294906 + j-0.07074228575985561
</pre>




```python
abs(a), abs(b)
```




<pre>
    (2.23606797749979, 5.0)
</pre>




```python
a>b
```




<pre>
    False
</pre>




```python
c=a+b
```


```python
c.kutupsal()
```




<pre>
    (5.084513097803541, 138.52080304179407)
</pre>


