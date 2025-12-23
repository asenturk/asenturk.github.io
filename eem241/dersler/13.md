# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 13 - OpenCV (2. ders)


<https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html>



```python
import cv2
import numpy as np
```


```python
img=cv2.imread("images/image.jpg")
```


```python
cv2.imshow('image',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


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
temp=np.ones(shape=(280,450,3), dtype="uint8")*50
temp[:2]
```




<pre>
    array([[[50, 50, 50],
            [50, 50, 50],
            [50, 50, 50],
            ...,
            [50, 50, 50],
            [50, 50, 50],
            [50, 50, 50]],
    
           [[50, 50, 50],
            [50, 50, 50],
            [50, 50, 50],
            ...,
            [50, 50, 50],
            [50, 50, 50],
            [50, 50, 50]]], dtype=uint8)
</pre>



### Toplama Çıkarma


```python
img1=img+temp
cv2.imshow('image',img)
cv2.imshow('image1',img1)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img1=cv2.add(img,temp)
cv2.imshow('image',img)
cv2.imshow('image1',img1)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img1=cv2.subtract(img,temp)
cv2.imshow('image',img)
cv2.imshow('image1',img1)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Çizgi


```python
pt1=(100,100)
pt2=(400,200)
color=(0,255,0)
thickness=2

img2=cv2.line(img, pt1, pt2, color, thickness)

cv2.imshow('image1',img2)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
x=np.zeros(shape=(300,400), dtype="uint8")
cv2.imshow('x',x)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
cv2.line(x, (50,100), (250,100), 255,2)
cv2.line(x, (250,100), (250,200), 255,2)
cv2.line(x, (250,200), (50,200), 255,2)
cv2.line(x, (50,200), (50,100), 255,2)

x[102:198,52:248]=170

cv2.imshow('image1',x)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")

tiklama_sayisi=0
x1, y1=None, None
x2, y2=None, None

def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi, x1,y1,x2,y2
    global img
    if event == cv2.EVENT_LBUTTONDOWN:
        if tiklama_sayisi == 0:
            x1 = x
            y1 = y
            print("1:",x1, y1)
        if tiklama_sayisi == 1:
            x2 = x
            y2 = y
            print("2:",x2, y2)
            cv2.line(img, (x1,y1), (x2,y2), (0,0,255), 2);
            cv2.imshow('Resim',img)
       
        tiklama_sayisi += 1
        
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    1: 76 45
    2: 359 218
</pre>
    

### Dikdörtgen


```python
img=cv2.imread("images/image.jpg")
cv2.rectangle(img, (50,50),(350,200),(0,255,0),3)
cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")

tiklama_sayisi=0
x1, y1=None, None
x2, y2=None, None

def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi, x1,y1,x2,y2
    global img
    if event == cv2.EVENT_LBUTTONDOWN:
        if tiklama_sayisi == 0:
            x1 = x
            y1 = y
            print("1:",x1, y1)
        if tiklama_sayisi == 1:
            x2 = x
            y2 = y
            print("2:",x2, y2)
            cv2.rectangle(img, (x1,y1),(x2,y2),(0,255,0),3)
            cv2.imshow('Resim',img)
       
        tiklama_sayisi += 1
        
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    1: 83 228
    2: 136 275
</pre>
    

### Daire


```python
img=cv2.imread("images/image.jpg")
cv2.circle(img, (100,200), 50, (255,0,0),2)
cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")
cv2.circle(img, (100,200), 50, (255,0,0),-1)
cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")

tiklama_sayisi=0
x1, y1=None, None
x2, y2=None, None

def mouse_event(event,x,y,flags,param):
    global tiklama_sayisi, x1,y1,x2,y2
    global img
    if event == cv2.EVENT_LBUTTONDOWN:
        if tiklama_sayisi == 0:
            x1 = x
            y1 = y
            print("merkez:",x1, y1)
        if tiklama_sayisi == 1:
            x2 = x
            y2 = y
            print("2:",x2, y2)
            yaricap = int(np.sqrt((x1-x2)**2+(y1-y2)**2))
            cv2.circle(img, (x1,y1),yaricap,(0,255,0),3)
            cv2.imshow('Resim',img)
       
        tiklama_sayisi += 1
        
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

<pre>
    merkez: 199 85
    2: 225 82
</pre>
    

### Yazı yazma


```python
img=cv2.imread("images/image.jpg")

cv2.putText(img, "Messi", (160,50), cv2.FONT_HERSHEY_PLAIN, 3, (255,0,255), 2)

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")

def mouse_event(event,x,y,flags,param):
    if event == cv2.EVENT_LBUTTONDOWN:
        b,g,r=img[y,x,:]
        cv2.putText(img, f"x:{x} y:{y} ({b},{g},{r})", (x,y-5), cv2.FONT_HERSHEY_PLAIN, 1.5, (255,0,255), 2)
        
        cv2.imshow('Resim',img)
       
cv2.imshow('Resim',img)
cv2.setMouseCallback('Resim',mouse_event)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Boyutlandırma


```python
img=cv2.imread("images/image.jpg")
h, w, c = img.shape

img=cv2.resize(img,(300,150))

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
yeni_yukseklik = 200
oran = yeni_yukseklik/h
yeni_genislik = int(oran * w)

img=cv2.imread("images/image.jpg")
img=cv2.resize(img,(yeni_genislik,yeni_yukseklik))

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")
img=cv2.resize(img,(None,None),fx=0.3, fy=0.3)

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img=cv2.imread("images/image.jpg")
img=cv2.resize(img,(None,None),fx=2, fy=2)

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Bit düzey işlemler


```python
img=np.zeros((400,600), dtype="uint8")
cv2.rectangle(img,(50,50),(300,350),255,-1)

cv2.circle(img, (350,200),150, 255,-1)

cv2.imshow('Resim',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
img1=np.zeros((400,600), dtype="uint8")
cv2.rectangle(img1,(50,50),(300,350),255,-1)

img2=np.zeros((400,600), dtype="uint8")
cv2.circle(img2, (350,200),150, 255,-1)

b_and=cv2.bitwise_and(img1, img2)
b_or=cv2.bitwise_or(img1, img2)
b_xor=cv2.bitwise_xor(img1, img2)
b_not=cv2.bitwise_not(img1)

cv2.imshow('and',b_and)
cv2.imshow('or',b_or)
cv2.imshow('xor',b_xor)
cv2.imshow('not',b_not)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Filtreleme


```python
kernel_3_3 = np.ones((3,3), dtype="float32")/9
kernel_3_3
```




<pre>
    array([[0.11111111, 0.11111111, 0.11111111],
           [0.11111111, 0.11111111, 0.11111111],
           [0.11111111, 0.11111111, 0.11111111]], dtype=float32)
</pre>




```python
img=cv2.imread("images/image.jpg")
img_f=cv2.filter2D(img,-1, kernel=kernel_3_3)
```


```python
cv2.imshow('image',img)
cv2.imshow('image_f',img_f)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Eşikleme


gradient .jpg dosyasını indirmek için [tıklayınız.](files/gradient.jpg)

```python
img=cv2.imread("images/gradient.jpg",0)

cv2.imshow('image',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```python
th, img1=cv2.threshold(img,127,255, cv2.THRESH_BINARY)
th, img2=cv2.threshold(img,127,255, cv2.THRESH_BINARY_INV)

cv2.imshow('image',img)
cv2.imshow('image1',img1)
cv2.imshow('image2',img2)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Kameradan görüntü almak için


```python
import cv2
cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    cv2.imshow('Video', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

### Kameradan alınan görüntüyü çizime dönüştüren program


```python
import cv2
cap = cv2.VideoCapture(0)

while True:
    ret, img = cap.read()
    
    img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    
    # filtre
    img_f=cv2.filter2D(img_gray,-1, kernel=kernel_3_3)
    
    # kenar bulma algoritması
    kenarlar=cv2.Canny(img_f,10,70)
    
    th, th_image=cv2.threshold(kenarlar,70,255, cv2.THRESH_BINARY_INV)
    
    cv2.imshow('Video', kenarlar)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```
