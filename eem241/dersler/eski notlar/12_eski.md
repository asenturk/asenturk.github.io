# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 12 - OpenCV (1. ders)

```python
import cv2
import numpy as np
```

Bu çalışmada images klasöründe bulunan image.jpg görüntüsü kullanılmıştır. İndirmek için [tıklayınız](./files/image.jpg). 


```python
img=cv2.imread("images/image.jpg")
```

- opencv bir görüntüyü BGR formatında okur.

```python
img
```




<pre>
    array([[[ 37,  40,  48],
            [ 42,  45,  53],
            [ 43,  49,  56],
            ...,
            [ 55,  55,  55],
            [ 53,  53,  53],
            [ 53,  53,  53]],
    
           [[ 40,  43,  51],
            [ 44,  47,  55],
            [ 46,  52,  59],
            ...,
            [ 59,  59,  59],
            [ 58,  57,  59],
            [ 56,  58,  58]],
    
           [[ 41,  46,  55],
            [ 47,  52,  61],
            [ 52,  57,  66],
            ...,
            [ 63,  65,  66],
            [ 62,  63,  67],
            [ 59,  63,  64]],
    
           ...,
    
           [[ 52, 137,  93],
            [ 45, 130,  86],
            [ 40, 125,  81],
            ...,
            [ 53, 127,  85],
            [ 57, 130,  90],
            [ 57, 130,  90]],
    
           [[ 58, 140,  97],
            [ 60, 142,  99],
            [ 51, 133,  90],
            ...,
            [ 58, 132,  90],
            [ 64, 137,  97],
            [ 64, 137,  97]],
    
           [[ 52, 134,  91],
            [ 60, 142,  99],
            [ 49, 131,  88],
            ...,
            [ 57, 131,  89],
            [ 52, 125,  85],
            [ 52, 125,  85]]], dtype=uint8)
</pre>



- Resmi bir pencerede görüntülemek için:


```python
cv2.imshow('image',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
- okunan görüntüyü bilgisayara kaydetmek için:
```


```python
cv2.imwrite("a.png", img)
```




    True




```python
type(img)
```




<pre>
    numpy.ndarray
</pre>




```python
img.shape
```




<pre>
    (280, 450, 3)
</pre>




```python
img.dtype
```




<pre>
    dtype('uint8')
</pre>




```python
# bir pikselin alabileceği farklı değerleri sayısı:
256*256*256
```




<pre>
    16777216
</pre>




```python
280*450*3
```




<pre>
    378000
</pre>




```python
img.size
```




<pre>
    378000
</pre>




```python
yukseklik, genislik, kanal = img.shape
yukseklik, genislik, kanal
```




<pre>
    (280, 450, 3)
</pre>



- Görüntüyü gri tonlamalı olarak okumak için:


```python
img_g=cv2.imread("images/image.jpg",0)
img_g.shape
```




<pre>
    (280, 450)
</pre>




```python
cv2.imshow('image',img_g)
cv2.waitKey(0)
cv2.destroyAllWindows()
```




```python
img[:3,:3,:]
```




<pre>
    array([[[37, 40, 48],
            [42, 45, 53],
            [43, 49, 56]],
    
           [[40, 43, 51],
            [44, 47, 55],
            [46, 52, 59]],
    
           [[41, 46, 55],
            [47, 52, 61],
            [52, 57, 66]]], dtype=uint8)
</pre>




```python
img_g[:3,:3]
```




<pre>
    array([[42, 47, 50],
           [45, 49, 53],
           [48, 54, 59]], dtype=uint8)
</pre>



- fareye tıklama olaylarının algılanması için aşağıdaki şablon programı kullanacağız.


```python
def mouse_event(event,x,y,flags,param):
    if event == cv2.EVENT_LBUTTONDOWN:
        print(x,y)
 
img=cv2.imread("images/image.jpg")
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    67 58
    290 71
    200 139
</pre>
    


```python
def mouse_event(event,x,y,flags,param):
    if event == cv2.EVENT_LBUTTONDOWN:
        print(x,y)
        print(f"x:{x},y:{y} koordinatındaki piksel değeri:\n {img[y,x]}")
 
img=cv2.imread("images/image.jpg")
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    23 10
    x:23,y:10 koordinatındaki piksel değeri:
     [ 9 10  8]
    372 259
    x:372,y:259 koordinatındaki piksel değeri:
     [217 230 222]
    214 165
    x:214,y:165 koordinatındaki piksel değeri:
     [ 73  37 175]
    217 251
    x:217,y:251 koordinatındaki piksel değeri:
     [152  59  38]
    53 241
    x:53,y:241 koordinatındaki piksel değeri:
     [ 37 140  89]
    116 255
    x:116,y:255 koordinatındaki piksel değeri:
     [ 78 245 236]
</pre>
    

- bir piksel değerine ulaşmak için:


```python
img[255,116]
```




<pre>
    array([ 78, 245, 236], dtype=uint8)
</pre>



- resmi bgr formatından gri tonlamalı renge çevirmek için:


```python
img_gray= cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
img_gray
```




<pre>
    array([[ 42,  47,  50, ...,  55,  53,  53],
           [ 45,  49,  53, ...,  59,  58,  58],
           [ 48,  54,  59, ...,  65,  64,  63],
           ...,
           [114, 107, 102, ..., 106, 110, 110],
           [118, 120, 111, ..., 111, 117, 117],
           [112, 120, 109, ..., 110, 105, 105]], dtype=uint8)
</pre>




```python
def mouse_event(event,x,y,flags,param):
    if event == cv2.EVENT_LBUTTONDOWN:
        print(x,y)
        print(f"x:{x},y:{y} koordinatındaki piksel değeri:\n {img[y,x]}")
        print(f"koordinatlardaki grayscale piksel değeri: {img_gray[y,x]}")
 
img=cv2.imread("images/image.jpg")
img_gray= cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    374 264
    x:374,y:264 koordinatındaki piksel değeri:
     [222 233 225]
    koordinatlardaki grayscale piksel değeri: 229
    207 22
    x:207,y:22 koordinatındaki piksel değeri:
     [27 20 17]
    koordinatlardaki grayscale piksel değeri: 20
</pre>
    

- görüntünü bir parçası


```python
img=cv2.imread("images/image.jpg")
part=img[100:270, 120:280, :]


cv2.imshow('Parça',part)
cv2.waitKey(0)
cv2.destroyAllWindows()
```




```python
tiklama_sayisi=0

def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi
    if event == cv2.EVENT_LBUTTONDOWN:
        tiklama_sayisi += 1
 
img=cv2.imread("images/image.jpg")
img_gray= cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
print(tiklama_sayisi)
```

<pre>
    10
</pre>
    


```python
tiklama_sayisi=0

sol_ust_i=None
sol_ust_j=None
sag_alt_i=None
sag_alt_j=None

def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi, sol_ust_i, sol_ust_j, sag_alt_i, sag_alt_j
    if event == cv2.EVENT_LBUTTONDOWN:
        if tiklama_sayisi == 0:
            sol_ust_i = y
            sol_ust_j = x
            
            print("0",sol_ust_i, sol_ust_j)
    
        if tiklama_sayisi == 1:
            sag_alt_i = y
            sag_alt_j = x
            
            print("1",sag_alt_i, sag_alt_j)
        
        tiklama_sayisi += 1  
 
img=cv2.imread("images/image.jpg")
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()

parca = img[sol_ust_i:sag_alt_i, sol_ust_j:sag_alt_j, :]

cv2.imshow('Parça',parca)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    0 56 168
    1 106 218
</pre>
    

- resim üzerindeki bir parçayı başka bir yere yapıştırmak


```python
img[56:106, 300:350] = parca
```


```python
cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img[56:106, 300:350] = parca
img[56:106,168:218]=255
```


```python
cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

- sol üst, sağ alt koordinatlara tıklanması sonrası elde edilen bölgeyi 3. tıklanılan yere yapıştıran kod.


```python
tiklama_sayisi=0

sol_ust_i=None
sol_ust_j=None
sag_alt_i=None
sag_alt_j=None


def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi, sol_ust_i, sol_ust_j, sag_alt_i, sag_alt_j
    global img
    if event == cv2.EVENT_LBUTTONDOWN:
        if tiklama_sayisi == 0:
            sol_ust_i = y
            sol_ust_j = x
            
            print("0",sol_ust_i, sol_ust_j)
    
        if tiklama_sayisi == 1:
            sag_alt_i = y
            sag_alt_j = x
            
            print("1",sag_alt_i, sag_alt_j)
            
        if tiklama_sayisi == 2:
            genislik = sag_alt_j-sol_ust_j
            yukseklik = sag_alt_i - sol_ust_i
            i=y
            j=x
            img[i:i+yukseklik, j:j+genislik]  = img[sol_ust_i:sag_alt_i,sol_ust_j:sag_alt_j]
            
        tiklama_sayisi += 1
 
img=cv2.imread("images/image.jpg")
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()


cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    0 221 82
    1 269 142
</pre>
   