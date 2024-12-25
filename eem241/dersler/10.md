# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 10 - NumPy


```
pip install numpy
```

```python
import numpy as np

my_list = [1,2,3]
my_list
```




<pre>
    [1, 2, 3]
</pre>




```python
np.array(my_list,)
```




<pre>
    array([1, 2, 3])
</pre>




```python
my_matrix = [[1,2,3],[4,5,6],[7,8,9]]
my_matrix
```




<pre>
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
</pre>




```python
np.array(my_matrix)
```




<pre>
    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])
</pre>



### arange


```python
np.arange(0,10)
```




<pre>
    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
</pre>




```python
np.arange(0,11,2)
```




<pre>
    array([ 0,  2,  4,  6,  8, 10])
</pre>



### sıfırlar ve birler


```python
np.zeros(3)
```




<pre>
    array([0., 0., 0.])
</pre>




```python
np.zeros((5,5))
```




<pre>
    array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])
</pre>




```python
np.ones(3)
```




<pre>
    array([1., 1., 1.])
</pre>




```python
np.ones((3,3))
```




<pre>
    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])
</pre>



### linspace


```python
np.linspace(0,10,3)
```




<pre>
    array([ 0.,  5., 10.])
</pre>




```python
np.linspace(0,1,9)
```




<pre>
    array([0.   , 0.125, 0.25 , 0.375, 0.5  , 0.625, 0.75 , 0.875, 1.   ])
</pre>



## Random 


### rand
``[0, 1)`` arasında değerler


```python
np.random.rand(2)
```




<pre>
    array([0.91425598, 0.13678438])
</pre>




```python
np.random.rand(2,3)
```




<pre>
    array([[0.49006695, 0.87254349, 0.04637703],
           [0.98931526, 0.77884387, 0.00985389]])
</pre>



### randint
``[düşük, yüksek)`` tamsayılar arasında


```python
np.random.randint(1,100)
```




<pre>
    61
</pre>




```python
np.random.randint(1,100,10)
```




<pre>
    array([54, 56,  9, 80, 16, 50, 74, 67, 34, 71])
</pre>




```python
np.random.randint(1,100,(2,3))
```




<pre>
    array([[51, 96, 35],
           [18, 92, 23]])
</pre>








## max min argmax argmin

```python
ranarr = np.random.randint(0,50,10)
ranarr
```




<pre>
    array([16, 42, 42, 38, 27,  5,  0,  4, 24, 37])
</pre>


```python
ranarr.max()
```




<pre>
    42
</pre>




```python
ranarr.argmax()
```




<pre>
    1
</pre>




```python
ranarr.min()
```




<pre>
    0
</pre>




```python
ranarr.argmin()
```




<pre>
    6
</pre>



## Shape Reshape
```python
arr = np.arange(25)
arr
```




<pre>
    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23, 24])
</pre>











```python
arr.reshape(5,5)
```


    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])


```python
arr = np.arange(25)
arr.shape
```




<pre>
    (25,)
</pre>




```python
arr.reshape(1,25)
```




<pre>
    array([[ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15,
            16, 17, 18, 19, 20, 21, 22, 23, 24]])
</pre>







```python
arr.reshape(25,1)
```




<pre>
    array([[ 0],
           [ 1],
           [ 2],
           [ 3],
           [ 4],
           [ 5],
           [ 6],
           [ 7],
           [ 8],
           [ 9],
           [10],
           [11],
           [12],
           [13],
           [14],
           [15],
           [16],
           [17],
           [18],
           [19],
           [20],
           [21],
           [22],
           [23],
           [24]])
</pre>






```python
arr=np.arange(0,20)
arr
```




<pre>
    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19])
</pre>




```python
a=arr.reshape(10,-1)
a
```




<pre>
    array([[ 0,  1],
           [ 2,  3],
           [ 4,  5],
           [ 6,  7],
           [ 8,  9],
           [10, 11],
           [12, 13],
           [14, 15],
           [16, 17],
           [18, 19]])
</pre>




```python
a.shape
```




<pre>
    (10, 2)
</pre>




```python
b=arr.reshape(4,-1)
b.shape
```




<pre>
    (4, 5)
</pre>

# indeks


```python
arr = np.arange(0,5.1,0.5)
arr
```




<pre>
    array([0. , 0.5, 1. , 1.5, 2. , 2.5, 3. , 3.5, 4. , 4.5, 5. ])
</pre>




```python
arr[8]
```




<pre>
    4.0
</pre>




```python
arr[1:5]
```




<pre>
    array([0.5, 1. , 1.5, 2. ])
</pre>




```python
arr[0:5]
```




<pre>
    array([0. , 0.5, 1. , 1.5, 2. ])
</pre>



## Atama


```python
arr[0]=10
arr[1:5]=100
arr
```




<pre>
    array([ 10. , 100. , 100. , 100. , 100. ,   2.5,   3. ,   3.5,   4. ,
             4.5,   5. ])
</pre>




```python
arr = np.arange(0,11)
arr
```




<pre>
    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])
</pre>




```python
slice_of_arr = arr[0:6]
slice_of_arr
```




<pre>
    array([0, 1, 2, 3, 4, 5])
</pre>




```python
slice_of_arr[:]=99
slice_of_arr
```




<pre>
    array([99, 99, 99, 99, 99, 99])
</pre>



Orjinal dizi:


```python
arr
```




<pre>
    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])
</pre>




```python
arr_copy = arr.copy()
arr_copy
```




<pre>
    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])
</pre>



## Çok boyutlu diziler


```python
arr_2d = np.array(([5,10,15],[20,25,30],[35,40,45]))
arr_2d
```




<pre>
    array([[ 5, 10, 15],
           [20, 25, 30],
           [35, 40, 45]])
</pre>




```python
arr_2d[1]
```




<pre>
    array([20, 25, 30])
</pre>




```python
arr_2d[1][0]
```




<pre>
    20
</pre>




```python
arr_2d[1,0]
```




<pre>
    20
</pre>




```python
arr_2d[:2,1:]
```




<pre>
    array([[10, 15],
           [25, 30]])
</pre>




```python
arr_2d[2]
```




<pre>
    array([35, 40, 45])
</pre>




```python
arr_2d[2,:]
```




<pre>
    array([35, 40, 45])
</pre>




```python
arr2d = np.zeros((10,10))
arr_length = arr2d.shape[1]
for i in range(arr_length):
    arr2d[i] = i   
arr2d
```




<pre>
    array([[0., 0., 0., 0., 0., 0., 0., 0., 0., 0.],
           [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [2., 2., 2., 2., 2., 2., 2., 2., 2., 2.],
           [3., 3., 3., 3., 3., 3., 3., 3., 3., 3.],
           [4., 4., 4., 4., 4., 4., 4., 4., 4., 4.],
           [5., 5., 5., 5., 5., 5., 5., 5., 5., 5.],
           [6., 6., 6., 6., 6., 6., 6., 6., 6., 6.],
           [7., 7., 7., 7., 7., 7., 7., 7., 7., 7.],
           [8., 8., 8., 8., 8., 8., 8., 8., 8., 8.],
           [9., 9., 9., 9., 9., 9., 9., 9., 9., 9.]])
</pre>




```python
arr2d[[2,4,6,8]]
```


<pre>
    array([[ 2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.],
           [ 4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.],
           [ 6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.],
           [ 8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.]])
</pre>



```python
arr2d[[6,4,2,7]]
```




<pre>
    array([[6., 6., 6., 6., 6., 6., 6., 6., 6., 6.],
           [4., 4., 4., 4., 4., 4., 4., 4., 4., 4.],
           [2., 2., 2., 2., 2., 2., 2., 2., 2., 2.],
           [7., 7., 7., 7., 7., 7., 7., 7., 7., 7.]])
</pre>



## Karşılaştırma


```python
arr = np.arange(1,11)
arr
```




<pre>
    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])
</pre>




```python
arr > 4
```




<pre>
    array([False, False, False, False,  True,  True,  True,  True,  True,
            True])
</pre>




```python
bool_arr = arr>4
bool_arr
```




<pre>
    array([False, False, False, False,  True,  True,  True,  True,  True,
            True])
</pre>




```python
arr[bool_arr]
```




<pre>
    array([ 5,  6,  7,  8,  9, 10])
</pre>




```python
arr[arr>2]
```




<pre>
    array([ 3,  4,  5,  6,  7,  8,  9, 10])
</pre>





# Aritmetik İşlemler





```python
arr = np.arange(0,10)
```


```python
arr + arr
```




<pre>
    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])
</pre>




```python
arr * arr
```




<pre>
    array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])
</pre>




```python
arr - arr
```




<pre>
    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])
</pre>




```python
arr/arr
```

<pre>
    D:\Temps\Temp\ipykernel_12020\1862401812.py:1: RuntimeWarning: invalid value encountered in true_divide
      arr/arr
</pre>
    




<pre>
    array([nan,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.])
</pre>




```python
1/arr
```

<pre>
    D:\Temps\Temp\ipykernel_12020\255282349.py:1: RuntimeWarning: divide by zero encountered in true_divide
      1/arr
    




    array([       inf, 1.        , 0.5       , 0.33333333, 0.25      ,
           0.2       , 0.16666667, 0.14285714, 0.125     , 0.11111111])
</pre>




```python
arr**3
```




<pre>
    array([  0,   1,   8,  27,  64, 125, 216, 343, 512, 729], dtype=int32)
</pre>



## matris çarpımı


```python
a=np.random.randint(0,20,(4,3))
a
```




<pre>
    array([[13, 17,  1],
           [19, 14, 10],
           [16,  2, 19],
           [ 8, 15, 12]])
</pre>




```python
b=np.random.randint(0,20,(3,5))
b
```




<pre>
    array([[ 5,  1, 12,  6, 15],
           [ 2,  3,  6, 18, 18],
           [13,  9,  3, 19, 18]])
</pre>




```python
np.matmul(a,b)
```




<pre>
    array([[112,  73, 261, 403, 519],
           [253, 151, 342, 556, 717],
           [331, 193, 261, 493, 618],
           [226, 161, 222, 546, 606]])
</pre>




```python
a@b
```




<pre>
    array([[112,  73, 261, 403, 519],
           [253, 151, 342, 556, 717],
           [331, 193, 261, 493, 618],
           [226, 161, 222, 546, 606]])
</pre>



##  Dizi fonksiyonları

[universal array functions](http://docs.scipy.org/doc/numpy/reference/ufuncs.html)


```python
np.sqrt(arr)
```




<pre>
    array([0.        , 1.        , 1.41421356, 1.73205081, 2.        ,
           2.23606798, 2.44948974, 2.64575131, 2.82842712, 3.        ])
</pre>




```python
#e^
np.exp(arr)
```




<pre>
    array([1.00000000e+00, 2.71828183e+00, 7.38905610e+00, 2.00855369e+01,
           5.45981500e+01, 1.48413159e+02, 4.03428793e+02, 1.09663316e+03,
           2.98095799e+03, 8.10308393e+03])
</pre>




```python
np.max(arr) 
```




<pre>
    9
</pre>




```python
np.sin(arr)
```


<pre>
    array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ,
           -0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849])
</pre>


## determinant  ve n bilinmeyenli denklemin çözümü


```python
A=np.array([[1,1,1],[2,1,2],[1,2,3]])
y=np.array([9,15,20])
```


```python
from numpy.linalg import solve
from numpy.linalg import det
```


```python
det(A)
```




<pre>
    -1.9999999999999993
</pre>




```python
solve(A,y)
```




<pre>
    array([2., 3., 4.])
</pre>
