
- Yapay sinir ağları ile ilgili slaytı indirmek için [tıklayınız](images/04.pptx).

## Yakıt Verimliliği Çalışması
Bu çalışmada yakıt verimliliği ile aşağıdaki sayfada verilen eğitim üzerine çalışmalar yapılmıştır.

https://www.tensorflow.org/tutorials/keras/regression

Veri setini indirmek için [tıklayınız](images/04_auto-mpg.data).


```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd # pip install pandas
```


```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers
```


```python
column_names = ['MPG', 'Cylinders', 'Displacement', 'Horsepower', 'Weight',
                'Acceleration', 'Model Year', 'Origin']
dataset=pd.read_csv("04_auto-mpg.data", names=column_names, na_values='?',
                   comment='\t', sep=' ', skipinitialspace=True)
dataset
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MPG</th>
      <th>Cylinders</th>
      <th>Displacement</th>
      <th>Horsepower</th>
      <th>Weight</th>
      <th>Acceleration</th>
      <th>Model Year</th>
      <th>Origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504.0</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693.0</td>
      <td>11.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436.0</td>
      <td>11.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433.0</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449.0</td>
      <td>10.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>27.0</td>
      <td>4</td>
      <td>140.0</td>
      <td>86.0</td>
      <td>2790.0</td>
      <td>15.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52.0</td>
      <td>2130.0</td>
      <td>24.6</td>
      <td>82</td>
      <td>2</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295.0</td>
      <td>11.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79.0</td>
      <td>2625.0</td>
      <td>18.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720.0</td>
      <td>19.4</td>
      <td>82</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>398 rows × 8 columns</p>
</div>




```python
dataset.isna().sum()
```




    MPG             0
    Cylinders       0
    Displacement    0
    Horsepower      6
    Weight          0
    Acceleration    0
    Model Year      0
    Origin          0
    dtype: int64




```python
# clean data
dataset = dataset.dropna()
```


```python
dataset
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MPG</th>
      <th>Cylinders</th>
      <th>Displacement</th>
      <th>Horsepower</th>
      <th>Weight</th>
      <th>Acceleration</th>
      <th>Model Year</th>
      <th>Origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504.0</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693.0</td>
      <td>11.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436.0</td>
      <td>11.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433.0</td>
      <td>12.0</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449.0</td>
      <td>10.5</td>
      <td>70</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>27.0</td>
      <td>4</td>
      <td>140.0</td>
      <td>86.0</td>
      <td>2790.0</td>
      <td>15.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52.0</td>
      <td>2130.0</td>
      <td>24.6</td>
      <td>82</td>
      <td>2</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295.0</td>
      <td>11.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79.0</td>
      <td>2625.0</td>
      <td>18.6</td>
      <td>82</td>
      <td>1</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720.0</td>
      <td>19.4</td>
      <td>82</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 8 columns</p>
</div>




```python
dataset_np= dataset.to_numpy()
dataset_np
```



<pre>
    array([[ 18. ,   8. , 307. , ...,  12. ,  70. ,   1. ],
           [ 15. ,   8. , 350. , ...,  11.5,  70. ,   1. ],
           [ 18. ,   8. , 318. , ...,  11. ,  70. ,   1. ],
           ...,
           [ 32. ,   4. , 135. , ...,  11.6,  82. ,   1. ],
           [ 28. ,   4. , 120. , ...,  18.6,  82. ,   1. ],
           [ 31. ,   4. , 119. , ...,  19.4,  82. ,   1. ]])
</pre>



```python
from sklearn.preprocessing import OneHotEncoder
```


```python
 # Son sütunu seç (kategori sütunu)
categorical_column = dataset_np[:, -1].reshape(-1, 1)

# One-hot encoder oluştur ve uygula
encoder = OneHotEncoder(sparse_output=False)
encoded_column = encoder.fit_transform(categorical_column)

# Sonucu orijinal veriyle birleştir
dataset_encoded = np.hstack((dataset_np[:, :-1], encoded_column))

print(dataset_encoded)
```
<pre>
    [[ 18.   8. 307. ...   1.   0.   0.]
     [ 15.   8. 350. ...   1.   0.   0.]
     [ 18.   8. 318. ...   1.   0.   0.]
     ...
     [ 32.   4. 135. ...   1.   0.   0.]
     [ 28.   4. 120. ...   1.   0.   0.]
     [ 31.   4. 119. ...   1.   0.   0.]]
</pre>    


```python
print(dataset_encoded[-5:,:])
```

    [[2.700e+01 4.000e+00 1.400e+02 8.600e+01 2.790e+03 1.560e+01 8.200e+01
      1.000e+00 0.000e+00 0.000e+00]
     [4.400e+01 4.000e+00 9.700e+01 5.200e+01 2.130e+03 2.460e+01 8.200e+01
      0.000e+00 1.000e+00 0.000e+00]
     [3.200e+01 4.000e+00 1.350e+02 8.400e+01 2.295e+03 1.160e+01 8.200e+01
      1.000e+00 0.000e+00 0.000e+00]
     [2.800e+01 4.000e+00 1.200e+02 7.900e+01 2.625e+03 1.860e+01 8.200e+01
      1.000e+00 0.000e+00 0.000e+00]
     [3.100e+01 4.000e+00 1.190e+02 8.200e+01 2.720e+03 1.940e+01 8.200e+01
      1.000e+00 0.000e+00 0.000e+00]]
    


```python
# Horsepower
hp = dataset_encoded[:,3]
mpg = dataset_encoded[:,0]
plt.scatter(hp, mpg, marker="+", color="red")
plt.xlabel("hp")
plt.ylabel('mpg')
plt.show()
```


    
![png](output_11_0.png)
    



```python
# Horsepower
weight = dataset_encoded[:,4]
mpg = dataset_encoded[:,0]
plt.scatter(weight, mpg, marker="+", color="blue")
plt.xlabel("weight")
plt.ylabel('mpg')
plt.show()
```


    
![png](images/04_output_12_0.png)
    


## Tek katman, tek nöron


```python
# input ve output
y = mpg  # İlk sütun (çıktı)
X = hp  # Geri kalan sütunlar (girdi)
```


```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```



```python
from sklearn.preprocessing import MinMaxScaler

# X_train için Min-Max ölçekleme
scaler_X = MinMaxScaler()
# hp
X_train_scaled = scaler_X.fit_transform(X_train.reshape((-1,1)))

# X_test'i aynı scaler ile dönüştür
X_test_scaled = scaler_X.transform(X_test.reshape((-1,1)))

# y_train için Min-Max ölçekleme
scaler_y = MinMaxScaler()
y_train_scaled = scaler_y.fit_transform(y_train.reshape(-1, 1))  # y vektör olduğu için reshape gerekli

# y_test'i aynı scaler ile dönüştür
y_test_scaled = scaler_y.transform(y_test.reshape(-1, 1))

```


```python
X_train_scaled.shape
```



<pre>
    (313, 1)
</pre>



```python
model = keras.models.Sequential([
    layers.Dense(units=1, input_shape=(1,)) # Linear Model
])
```


```python
model.summary()
```
<pre>
    Model: "sequential_10"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_12 (Dense)            (None, 1)                 2         
                                                                     
    =================================================================
    Total params: 2
    Trainable params: 2
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
model.compile(optimizer='adam', loss='mse')
```


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 23ms/step - loss: 0.1432 - val_loss: 0.1209
    Epoch 2/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.1381 - val_loss: 0.1165
    Epoch 3/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1334 - val_loss: 0.1124
    Epoch 4/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.1291 - val_loss: 0.1088
    Epoch 5/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1252 - val_loss: 0.1054
    Epoch 6/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1215 - val_loss: 0.1025
    Epoch 7/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.1183 - val_loss: 0.0998
    Epoch 8/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.1154 - val_loss: 0.0972
    Epoch 9/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1127 - val_loss: 0.0949
    Epoch 10/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1102 - val_loss: 0.0927
    Epoch 11/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1078 - val_loss: 0.0907
    Epoch 12/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1056 - val_loss: 0.0888
    Epoch 13/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1035 - val_loss: 0.0870
    Epoch 14/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.1014 - val_loss: 0.0852
    Epoch 15/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0995 - val_loss: 0.0835
    Epoch 16/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0977 - val_loss: 0.0819
    Epoch 17/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0958 - val_loss: 0.0803
    Epoch 18/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0941 - val_loss: 0.0788
    Epoch 19/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0925 - val_loss: 0.0773
    Epoch 20/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0908 - val_loss: 0.0759
    Epoch 21/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0892 - val_loss: 0.0745
    Epoch 22/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0876 - val_loss: 0.0731
    Epoch 23/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0862 - val_loss: 0.0717
    Epoch 24/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0847 - val_loss: 0.0704
    Epoch 25/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0832 - val_loss: 0.0692
    Epoch 26/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0818 - val_loss: 0.0679
    Epoch 27/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0805 - val_loss: 0.0667
    Epoch 28/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0791 - val_loss: 0.0655
    Epoch 29/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0779 - val_loss: 0.0644
    Epoch 30/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0766 - val_loss: 0.0633
    Epoch 31/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0754 - val_loss: 0.0621
    Epoch 32/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0742 - val_loss: 0.0611
    Epoch 33/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0730 - val_loss: 0.0600
    Epoch 34/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0718 - val_loss: 0.0590
    Epoch 35/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0707 - val_loss: 0.0580
    Epoch 36/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0696 - val_loss: 0.0570
    Epoch 37/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0685 - val_loss: 0.0560
    Epoch 38/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0674 - val_loss: 0.0551
    Epoch 39/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0664 - val_loss: 0.0542
    Epoch 40/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0654 - val_loss: 0.0532
    Epoch 41/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0644 - val_loss: 0.0523
    Epoch 42/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0634 - val_loss: 0.0514
    Epoch 43/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0624 - val_loss: 0.0506
    Epoch 44/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0615 - val_loss: 0.0498
    Epoch 45/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0605 - val_loss: 0.0490
    Epoch 46/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0596 - val_loss: 0.0481
    Epoch 47/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0588 - val_loss: 0.0473
    Epoch 48/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0579 - val_loss: 0.0466
    Epoch 49/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0570 - val_loss: 0.0458
    Epoch 50/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0562 - val_loss: 0.0451
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0554 - val_loss: 0.0444
    Epoch 52/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0546 - val_loss: 0.0437
    Epoch 53/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0538 - val_loss: 0.0430
    Epoch 54/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0530 - val_loss: 0.0423
    Epoch 55/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0523 - val_loss: 0.0416
    Epoch 56/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0515 - val_loss: 0.0409
    Epoch 57/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0508 - val_loss: 0.0403
    Epoch 58/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0501 - val_loss: 0.0397
    Epoch 59/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0493 - val_loss: 0.0390
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0486 - val_loss: 0.0384
    Epoch 61/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0480 - val_loss: 0.0379
    Epoch 62/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0473 - val_loss: 0.0373
    Epoch 63/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0467 - val_loss: 0.0367
    Epoch 64/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0460 - val_loss: 0.0361
    Epoch 65/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0454 - val_loss: 0.0356
    Epoch 66/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0448 - val_loss: 0.0351
    Epoch 67/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0442 - val_loss: 0.0346
    Epoch 68/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0436 - val_loss: 0.0341
    Epoch 69/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0430 - val_loss: 0.0336
    Epoch 70/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0424 - val_loss: 0.0331
    Epoch 71/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0419 - val_loss: 0.0326
    Epoch 72/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0413 - val_loss: 0.0321
    Epoch 73/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0408 - val_loss: 0.0317
    Epoch 74/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0403 - val_loss: 0.0312
    Epoch 75/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0397 - val_loss: 0.0308
    Epoch 76/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0393 - val_loss: 0.0303
    Epoch 77/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0387 - val_loss: 0.0299
    Epoch 78/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0383 - val_loss: 0.0295
    Epoch 79/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0378 - val_loss: 0.0291
    Epoch 80/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0373 - val_loss: 0.0287
    Epoch 81/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0368 - val_loss: 0.0283
    Epoch 82/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0364 - val_loss: 0.0279
    Epoch 83/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0359 - val_loss: 0.0276
    Epoch 84/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0355 - val_loss: 0.0272
    Epoch 85/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0351 - val_loss: 0.0268
    Epoch 86/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0347 - val_loss: 0.0265
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0343 - val_loss: 0.0261
    Epoch 88/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0338 - val_loss: 0.0258
    Epoch 89/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0334 - val_loss: 0.0255
    Epoch 90/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0331 - val_loss: 0.0252
    Epoch 91/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0327 - val_loss: 0.0249
    Epoch 92/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0323 - val_loss: 0.0246
    Epoch 93/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0319 - val_loss: 0.0243
    Epoch 94/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0316 - val_loss: 0.0240
    Epoch 95/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0312 - val_loss: 0.0237
    Epoch 96/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0309 - val_loss: 0.0234
    Epoch 97/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0306 - val_loss: 0.0232
    Epoch 98/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0302 - val_loss: 0.0229
    Epoch 99/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0299 - val_loss: 0.0226
    Epoch 100/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0296 - val_loss: 0.0224
  </pre>  


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_23_0.png)
    



```python
y_test_predict_scaled=model.predict(X_test_scaled)
```
<pre>
    3/3 [==============================] - 0s 3ms/step
</pre>    


```python
y_pred = scaler_y.inverse_transform(y_test_predict_scaled)
```


```python
y_test[:10]
```



<pre>
    array([26. , 21.6, 36.1, 26. , 27. , 28. , 13. , 26. , 19. , 29. ])
</pre>



```python
y_pred[:10]
```



<pre>
    array([[24.879032],
           [22.3061  ],
           [25.382433],
           [24.8231  ],
           [23.928167],
           [24.543432],
           [19.229767],
           [24.543432],
           [23.424765],
           [25.997698]], dtype=float32)
</pre>




```python
X_fake = np.linspace(50, 230, 200).reshape((-1,1))
X_fake_scaled = scaler_X.transform(X_fake)

y_fake_pred_scaled = model.predict(X_fake_scaled)

y_fake_pred=scaler_y.inverse_transform(y_fake_pred_scaled)
```
<pre>
    7/7 [==============================] - 0s 3ms/step
</pre>    


```python
plt.plot(X_fake, y_fake_pred)
plt.scatter(hp, mpg, marker="+", color="red")
plt.show()
```


    
![png](images/04_output_29_0.png)
    




## Aktivasyonsuz büyük model


```python
# DNN
model = keras.Sequential([
    layers.Dense(64,  input_shape=(1,)),
    layers.Dense(64),
    layers.Dense(1)
])
```


```python
model.compile(loss="mse", optimizer="adam")

model.summary()
```
<pre>
    Model: "sequential_11"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_13 (Dense)            (None, 64)                128       
                                                                     
     dense_14 (Dense)            (None, 64)                4160      
                                                                     
     dense_15 (Dense)            (None, 1)                 65        
                                                                     
    =================================================================
    Total params: 4,353
    Trainable params: 4,353
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 21ms/step - loss: 0.1110 - val_loss: 0.0613
    Epoch 2/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0525 - val_loss: 0.0222
    Epoch 3/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0214 - val_loss: 0.0166
    Epoch 4/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0191 - val_loss: 0.0210
    Epoch 5/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0196 - val_loss: 0.0173
    Epoch 6/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0194 - val_loss: 0.0171
    Epoch 7/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0174 - val_loss: 0.0152
    Epoch 8/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0176 - val_loss: 0.0160
    Epoch 9/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0174 - val_loss: 0.0158
    Epoch 10/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0161
    Epoch 11/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0185 - val_loss: 0.0182
    Epoch 12/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0187 - val_loss: 0.0153
    Epoch 13/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0191 - val_loss: 0.0154
    Epoch 14/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0181 - val_loss: 0.0158
    Epoch 15/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0189 - val_loss: 0.0186
    Epoch 16/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0186 - val_loss: 0.0163
    Epoch 17/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0182 - val_loss: 0.0153
    Epoch 18/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0181 - val_loss: 0.0156
    Epoch 19/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0163
    Epoch 20/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0183 - val_loss: 0.0162
    Epoch 21/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0156
    Epoch 22/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0184 - val_loss: 0.0160
    Epoch 23/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0185 - val_loss: 0.0169
    Epoch 24/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0155
    Epoch 25/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0174 - val_loss: 0.0158
    Epoch 26/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0174 - val_loss: 0.0156
    Epoch 27/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0182 - val_loss: 0.0176
    Epoch 28/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0158
    Epoch 29/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0157
    Epoch 30/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0156
    Epoch 31/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0174 - val_loss: 0.0155
    Epoch 32/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0184 - val_loss: 0.0155
    Epoch 33/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0181 - val_loss: 0.0158
    Epoch 34/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0163
    Epoch 35/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0181 - val_loss: 0.0175
    Epoch 36/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0188 - val_loss: 0.0162
    Epoch 37/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0194 - val_loss: 0.0156
    Epoch 38/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0175 - val_loss: 0.0162
    Epoch 39/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0179 - val_loss: 0.0158
    Epoch 40/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0190 - val_loss: 0.0159
    Epoch 41/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0188 - val_loss: 0.0159
    Epoch 42/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0163
    Epoch 43/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0154
    Epoch 44/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0179 - val_loss: 0.0166
    Epoch 45/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0158
    Epoch 46/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0174 - val_loss: 0.0158
    Epoch 47/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0167
    Epoch 48/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0179 - val_loss: 0.0153
    Epoch 49/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0153
    Epoch 50/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0159
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0167
    Epoch 52/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0178 - val_loss: 0.0155
    Epoch 53/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0161
    Epoch 54/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0177 - val_loss: 0.0167
    Epoch 55/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0182 - val_loss: 0.0163
    Epoch 56/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0154
    Epoch 57/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0155
    Epoch 58/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0155
    Epoch 59/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0163
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0181 - val_loss: 0.0159
    Epoch 61/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0180 - val_loss: 0.0156
    Epoch 62/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0174
    Epoch 63/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0155
    Epoch 64/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0160
    Epoch 65/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0155
    Epoch 66/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0175 - val_loss: 0.0161
    Epoch 67/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0167
    Epoch 68/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0182 - val_loss: 0.0159
    Epoch 69/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0186 - val_loss: 0.0155
    Epoch 70/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0183 - val_loss: 0.0154
    Epoch 71/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0164
    Epoch 72/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0180 - val_loss: 0.0159
    Epoch 73/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0174 - val_loss: 0.0158
    Epoch 74/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0174 - val_loss: 0.0157
    Epoch 75/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0177 - val_loss: 0.0158
    Epoch 76/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0161
    Epoch 77/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0156
    Epoch 78/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0156
    Epoch 79/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0166
    Epoch 80/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0155
    Epoch 81/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0175 - val_loss: 0.0163
    Epoch 82/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0179 - val_loss: 0.0158
    Epoch 83/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0160
    Epoch 84/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0175 - val_loss: 0.0153
    Epoch 85/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0161
    Epoch 86/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0180 - val_loss: 0.0178
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0179 - val_loss: 0.0153
    Epoch 88/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0177 - val_loss: 0.0158
    Epoch 89/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0176 - val_loss: 0.0160
    Epoch 90/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0177 - val_loss: 0.0161
    Epoch 91/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0156
    Epoch 92/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0181 - val_loss: 0.0161
    Epoch 93/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0172
    Epoch 94/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0180 - val_loss: 0.0150
    Epoch 95/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0178 - val_loss: 0.0156
    Epoch 96/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0176 - val_loss: 0.0165
    Epoch 97/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0177 - val_loss: 0.0165
    Epoch 98/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0181 - val_loss: 0.0156
    Epoch 99/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0179 - val_loss: 0.0153
    Epoch 100/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0182 - val_loss: 0.0156
</pre>    


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_35_0.png)
    



```python
y_test_predict_scaled=model.predict(X_test_scaled)
```
<pre>
    3/3 [==============================] - 0s 3ms/step
</pre>    


```python
y_pred = scaler_y.inverse_transform(y_test_predict_scaled)
```


```python
y_test[:10]
```



<pre>
    array([26. , 21.6, 36.1, 26. , 27. , 28. , 13. , 26. , 19. , 29. ])
</pre>



```python
y_pred[:10]
```



<pre>
    array([[29.274797],
           [22.273424],
           [30.642967],
           [29.121162],
           [26.68683 ],
           [28.362114],
           [13.90795 ],
           [28.362114],
           [25.316181],
           [32.31797 ]], dtype=float32)
</pre>



```python
X_fake = np.linspace(50, 230, 200).reshape((-1,1))
X_fake_scaled = scaler_X.transform(X_fake)

y_fake_pred_scaled = model.predict(X_fake_scaled)

y_fake_pred=scaler_y.inverse_transform(y_fake_pred_scaled)
```
<pre>
    7/7 [==============================] - 0s 2ms/step
</pre>    


```python
plt.plot(X_fake, y_fake_pred)
plt.scatter(hp, mpg, marker="+", color="red")
plt.show()
```


    
![png](images/04_output_41_0.png)
    


# Aktivasyonlu büyük model


```python
# DNN
model = keras.Sequential([
    layers.Dense(64, activation='relu', input_shape=(1,)),
    layers.Dense(64, activation='relu'),
    layers.Dense(1)
])
```


```python
model.compile(loss="mse", optimizer="adam")

model.summary()
```
<pre>
    Model: "sequential_12"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_16 (Dense)            (None, 64)                128       
                                                                     
     dense_17 (Dense)            (None, 64)                4160      
                                                                     
     dense_18 (Dense)            (None, 1)                 65        
                                                                     
    =================================================================
    Total params: 4,353
    Trainable params: 4,353
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 22ms/step - loss: 0.1405 - val_loss: 0.0941
    Epoch 2/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.1041 - val_loss: 0.0799
    Epoch 3/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0858 - val_loss: 0.0634
    Epoch 4/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0697 - val_loss: 0.0500
    Epoch 5/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0562 - val_loss: 0.0383
    Epoch 6/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0436 - val_loss: 0.0288
    Epoch 7/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0330 - val_loss: 0.0211
    Epoch 8/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0251 - val_loss: 0.0164
    Epoch 9/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0200 - val_loss: 0.0147
    Epoch 10/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0179 - val_loss: 0.0143
    Epoch 11/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0168 - val_loss: 0.0144
    Epoch 12/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0165 - val_loss: 0.0144
    Epoch 13/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0161 - val_loss: 0.0134
    Epoch 14/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0160 - val_loss: 0.0138
    Epoch 15/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0155 - val_loss: 0.0129
    Epoch 16/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0152 - val_loss: 0.0133
    Epoch 17/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0151 - val_loss: 0.0131
    Epoch 18/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0151 - val_loss: 0.0135
    Epoch 19/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0148 - val_loss: 0.0128
    Epoch 20/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0146 - val_loss: 0.0129
    Epoch 21/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0144 - val_loss: 0.0133
    Epoch 22/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0143 - val_loss: 0.0130
    Epoch 23/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0143 - val_loss: 0.0134
    Epoch 24/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0143 - val_loss: 0.0127
    Epoch 25/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0142 - val_loss: 0.0141
    Epoch 26/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0145 - val_loss: 0.0127
    Epoch 27/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0143 - val_loss: 0.0136
    Epoch 28/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0140 - val_loss: 0.0126
    Epoch 29/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0142 - val_loss: 0.0141
    Epoch 30/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0140 - val_loss: 0.0126
    Epoch 31/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0139 - val_loss: 0.0133
    Epoch 32/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0139 - val_loss: 0.0126
    Epoch 33/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0138 - val_loss: 0.0132
    Epoch 34/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0138 - val_loss: 0.0129
    Epoch 35/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0141 - val_loss: 0.0124
    Epoch 36/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0138 - val_loss: 0.0136
    Epoch 37/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0137 - val_loss: 0.0125
    Epoch 38/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0137 - val_loss: 0.0128
    Epoch 39/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0136 - val_loss: 0.0131
    Epoch 40/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0136 - val_loss: 0.0126
    Epoch 41/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0138 - val_loss: 0.0132
    Epoch 42/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0135 - val_loss: 0.0126
    Epoch 43/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0136 - val_loss: 0.0133
    Epoch 44/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0134 - val_loss: 0.0125
    Epoch 45/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0135 - val_loss: 0.0125
    Epoch 46/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0134 - val_loss: 0.0133
    Epoch 47/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0135 - val_loss: 0.0126
    Epoch 48/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0134 - val_loss: 0.0128
    Epoch 49/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0127
    Epoch 50/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0135 - val_loss: 0.0126
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0135 - val_loss: 0.0131
    Epoch 52/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0135 - val_loss: 0.0123
    Epoch 53/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0134 - val_loss: 0.0130
    Epoch 54/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0133 - val_loss: 0.0125
    Epoch 55/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0128
    Epoch 56/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0135 - val_loss: 0.0131
    Epoch 57/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0141 - val_loss: 0.0134
    Epoch 58/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0133 - val_loss: 0.0122
    Epoch 59/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0134 - val_loss: 0.0128
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0128
    Epoch 61/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0133 - val_loss: 0.0129
    Epoch 62/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0132 - val_loss: 0.0128
    Epoch 63/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0132
    Epoch 64/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0126
    Epoch 65/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0125
    Epoch 66/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0132 - val_loss: 0.0127
    Epoch 67/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0132 - val_loss: 0.0129
    Epoch 68/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0135 - val_loss: 0.0125
    Epoch 69/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0134 - val_loss: 0.0129
    Epoch 70/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0123
    Epoch 71/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0132
    Epoch 72/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0124
    Epoch 73/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0126
    Epoch 74/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0125
    Epoch 75/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0129
    Epoch 76/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0136 - val_loss: 0.0133
    Epoch 77/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0135 - val_loss: 0.0126
    Epoch 78/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0130
    Epoch 79/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0131 - val_loss: 0.0123
    Epoch 80/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0134
    Epoch 81/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0132 - val_loss: 0.0126
    Epoch 82/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0130
    Epoch 83/100
    10/10 [==============================] - 0s 12ms/step - loss: 0.0132 - val_loss: 0.0126
    Epoch 84/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0132 - val_loss: 0.0127
    Epoch 85/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0132 - val_loss: 0.0128
    Epoch 86/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0128
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0127
    Epoch 88/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0132 - val_loss: 0.0127
    Epoch 89/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0133 - val_loss: 0.0125
    Epoch 90/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0135
    Epoch 91/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0137 - val_loss: 0.0124
    Epoch 92/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0131
    Epoch 93/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0133 - val_loss: 0.0127
    Epoch 94/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0132 - val_loss: 0.0129
    Epoch 95/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0132 - val_loss: 0.0125
    Epoch 96/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0132 - val_loss: 0.0128
    Epoch 97/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0135
    Epoch 98/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0134 - val_loss: 0.0125
    Epoch 99/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0132 - val_loss: 0.0134
    Epoch 100/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0133 - val_loss: 0.0129
 </pre>   


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_46_0.png)
    



```python
y_test_predict_scaled=model.predict(X_test_scaled)
```
<pre>
    3/3 [==============================] - 0s 3ms/step
</pre>    


```python
y_pred = scaler_y.inverse_transform(y_test_predict_scaled)
```


```python
y_test[:10]
```



<pre>
    array([26. , 21.6, 36.1, 26. , 27. , 28. , 13. , 26. , 19. , 29. ])
</pre>



```python
y_pred[:10]
```



<pre>
    array([[32.31129 ],
           [19.190641],
           [34.19633 ],
           [31.933548],
           [25.983114],
           [30.077898],
           [14.251822],
           [30.077898],
           [22.63136 ],
           [35.136513]], dtype=float32)
</pre>



```python
X_fake = np.linspace(50, 230, 200).reshape((-1,1))
X_fake_scaled = scaler_X.transform(X_fake)

y_fake_pred_scaled = model.predict(X_fake_scaled)

y_fake_pred=scaler_y.inverse_transform(y_fake_pred_scaled)
```
<pre>
    7/7 [==============================] - 0s 3ms/step
</pre>    


```python
plt.plot(X_fake, y_fake_pred)
plt.scatter(hp, mpg, marker="+", color="red")
plt.show()
```


    
![png](images/04_output_52_0.png)
    


## Çoklu veri


```python
X = dataset_encoded[:,1:]
y = dataset_encoded[:,0]
```


```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```


```python
from sklearn.preprocessing import MinMaxScaler

# X_train için Min-Max ölçekleme
scaler_X = MinMaxScaler()
# hp
X_train_scaled = scaler_X.fit_transform(X_train)

# X_test'i aynı scaler ile dönüştür
X_test_scaled = scaler_X.transform(X_test)

# y_train için Min-Max ölçekleme
scaler_y = MinMaxScaler()
y_train_scaled = scaler_y.fit_transform(y_train.reshape(-1, 1))  # y vektör olduğu için reshape gerekli

# y_test'i aynı scaler ile dönüştür
y_test_scaled = scaler_y.transform(y_test.reshape(-1, 1))

```


```python
X_train_scaled.shape, X_test_scaled.shape, y_train.shape
```



<pre>
    ((313, 9), (79, 9), (313,))
</pre>


### Aktivasyon fonksiyonu olmayan model


```python
model = keras.models.Sequential([
    layers.Dense(units=32, input_shape=(9,)), # Linear Model
    layers.Dense(1)
])
```


```python
model.summary()
```
<pre>
    Model: "sequential_13"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_19 (Dense)            (None, 32)                320       
                                                                     
     dense_20 (Dense)            (None, 1)                 33        
                                                                     
    =================================================================
    Total params: 353
    Trainable params: 353
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
model.compile(optimizer='adam', loss='mse')
```


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 25ms/step - loss: 0.1336 - val_loss: 0.0811
    Epoch 2/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0663 - val_loss: 0.0381
    Epoch 3/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0298 - val_loss: 0.0159
    Epoch 4/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0153 - val_loss: 0.0110
    Epoch 5/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0115 - val_loss: 0.0114
    Epoch 6/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0115 - val_loss: 0.0119
    Epoch 7/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0112 - val_loss: 0.0113
    Epoch 8/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0109 - val_loss: 0.0106
    Epoch 9/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0108 - val_loss: 0.0101
    Epoch 10/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0104 - val_loss: 0.0099
    Epoch 11/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0103 - val_loss: 0.0098
    Epoch 12/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0102 - val_loss: 0.0098
    Epoch 13/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0100 - val_loss: 0.0097
    Epoch 14/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0098 - val_loss: 0.0095
    Epoch 15/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0097 - val_loss: 0.0094
    Epoch 16/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0096 - val_loss: 0.0093
    Epoch 17/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0095 - val_loss: 0.0091
    Epoch 18/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0093 - val_loss: 0.0093
    Epoch 19/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0092 - val_loss: 0.0093
    Epoch 20/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0092 - val_loss: 0.0092
    Epoch 21/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0090 - val_loss: 0.0088
    Epoch 22/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0090 - val_loss: 0.0089
    Epoch 23/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0089 - val_loss: 0.0088
    Epoch 24/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0089 - val_loss: 0.0088
    Epoch 25/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0088 - val_loss: 0.0087
    Epoch 26/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0087 - val_loss: 0.0086
    Epoch 27/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0086 - val_loss: 0.0087
    Epoch 28/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0085 - val_loss: 0.0086
    Epoch 29/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0084 - val_loss: 0.0085
    Epoch 30/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0085 - val_loss: 0.0086
    Epoch 31/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0084 - val_loss: 0.0086
    Epoch 32/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0084 - val_loss: 0.0083
    Epoch 33/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0083 - val_loss: 0.0085
    Epoch 34/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0083 - val_loss: 0.0083
    Epoch 35/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0084 - val_loss: 0.0082
    Epoch 36/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0083 - val_loss: 0.0085
    Epoch 37/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0084 - val_loss: 0.0084
    Epoch 38/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0083 - val_loss: 0.0084
    Epoch 39/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0082 - val_loss: 0.0084
    Epoch 40/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0082 - val_loss: 0.0082
    Epoch 41/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0082 - val_loss: 0.0083
    Epoch 42/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0081 - val_loss: 0.0080
    Epoch 43/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0085 - val_loss: 0.0081
    Epoch 44/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0083 - val_loss: 0.0086
    Epoch 45/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0082 - val_loss: 0.0085
    Epoch 46/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0081
    Epoch 47/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0079
    Epoch 48/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0081 - val_loss: 0.0083
    Epoch 49/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0081 - val_loss: 0.0081
    Epoch 50/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0081 - val_loss: 0.0081
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0081
    Epoch 52/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0081
    Epoch 53/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0083
    Epoch 54/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0076
    Epoch 55/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0082
    Epoch 56/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0081
    Epoch 57/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0081 - val_loss: 0.0080
    Epoch 58/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0079 - val_loss: 0.0080
    Epoch 59/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0080 - val_loss: 0.0079
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0079
    Epoch 61/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0080
    Epoch 62/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0079 - val_loss: 0.0081
    Epoch 63/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0079 - val_loss: 0.0081
    Epoch 64/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0080 - val_loss: 0.0080
    Epoch 65/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0082
    Epoch 66/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0084 - val_loss: 0.0083
    Epoch 67/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0082 - val_loss: 0.0087
    Epoch 68/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0081
    Epoch 69/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0080
    Epoch 70/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0080 - val_loss: 0.0076
    Epoch 71/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0082
    Epoch 72/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0081
    Epoch 73/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0078 - val_loss: 0.0080
    Epoch 74/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0078 - val_loss: 0.0079
    Epoch 75/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0077 - val_loss: 0.0078
    Epoch 76/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0078 - val_loss: 0.0077
    Epoch 77/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0078 - val_loss: 0.0079
    Epoch 78/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0079 - val_loss: 0.0081
    Epoch 79/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0078 - val_loss: 0.0077
    Epoch 80/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0078 - val_loss: 0.0078
    Epoch 81/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0079 - val_loss: 0.0083
    Epoch 82/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0081
    Epoch 83/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0081 - val_loss: 0.0081
    Epoch 84/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0079 - val_loss: 0.0075
    Epoch 85/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0079 - val_loss: 0.0080
    Epoch 86/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0078 - val_loss: 0.0077
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0078 - val_loss: 0.0082
    Epoch 88/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0075
    Epoch 89/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0078 - val_loss: 0.0080
    Epoch 90/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0079 - val_loss: 0.0080
    Epoch 91/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0082 - val_loss: 0.0081
    Epoch 92/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0081 - val_loss: 0.0079
    Epoch 93/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0078 - val_loss: 0.0076
    Epoch 94/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0078 - val_loss: 0.0078
    Epoch 95/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0078 - val_loss: 0.0080
    Epoch 96/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0079 - val_loss: 0.0082
    Epoch 97/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0079 - val_loss: 0.0077
    Epoch 98/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0080 - val_loss: 0.0078
    Epoch 99/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0079 - val_loss: 0.0079
    Epoch 100/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0080 - val_loss: 0.0079
 </pre>   


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_63_0.png)
    


###  Aktivasyonlu tek katman model


```python
model = keras.models.Sequential([
    layers.Dense(units=32, input_shape=(9,), activation='relu'),
    layers.Dense(1)
])
```


```python
model.summary()
```
<pre>
    Model: "sequential_15"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_23 (Dense)            (None, 32)                320       
                                                                     
     dense_24 (Dense)            (None, 1)                 33        
                                                                     
    =================================================================
    Total params: 353
    Trainable params: 353
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
model.compile(optimizer='adam', loss='mse')
```


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 21ms/step - loss: 0.0943 - val_loss: 0.0820
    Epoch 2/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0606 - val_loss: 0.0554
    Epoch 3/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0393 - val_loss: 0.0382
    Epoch 4/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0266 - val_loss: 0.0273
    Epoch 5/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0193 - val_loss: 0.0207
    Epoch 6/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0151 - val_loss: 0.0166
    Epoch 7/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0126 - val_loss: 0.0141
    Epoch 8/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0114 - val_loss: 0.0127
    Epoch 9/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0106 - val_loss: 0.0120
    Epoch 10/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0103 - val_loss: 0.0115
    Epoch 11/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0100 - val_loss: 0.0113
    Epoch 12/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0097 - val_loss: 0.0111
    Epoch 13/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0095 - val_loss: 0.0108
    Epoch 14/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0093 - val_loss: 0.0107
    Epoch 15/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0092 - val_loss: 0.0103
    Epoch 16/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0089 - val_loss: 0.0102
    Epoch 17/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0088 - val_loss: 0.0100
    Epoch 18/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0086 - val_loss: 0.0101
    Epoch 19/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0085 - val_loss: 0.0097
    Epoch 20/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0083 - val_loss: 0.0096
    Epoch 21/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0081 - val_loss: 0.0094
    Epoch 22/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0081 - val_loss: 0.0092
    Epoch 23/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0080 - val_loss: 0.0092
    Epoch 24/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0078 - val_loss: 0.0089
    Epoch 25/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0077 - val_loss: 0.0090
    Epoch 26/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0076 - val_loss: 0.0087
    Epoch 27/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0074 - val_loss: 0.0085
    Epoch 28/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0074 - val_loss: 0.0084
    Epoch 29/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0073 - val_loss: 0.0081
    Epoch 30/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0070 - val_loss: 0.0082
    Epoch 31/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0070 - val_loss: 0.0080
    Epoch 32/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0069 - val_loss: 0.0079
    Epoch 33/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0067 - val_loss: 0.0078
    Epoch 34/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0067 - val_loss: 0.0076
    Epoch 35/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0066 - val_loss: 0.0076
    Epoch 36/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0066 - val_loss: 0.0075
    Epoch 37/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0064 - val_loss: 0.0073
    Epoch 38/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0063 - val_loss: 0.0072
    Epoch 39/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0063 - val_loss: 0.0070
    Epoch 40/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0062 - val_loss: 0.0070
    Epoch 41/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0061 - val_loss: 0.0070
    Epoch 42/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0061 - val_loss: 0.0070
    Epoch 43/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0060 - val_loss: 0.0067
    Epoch 44/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0059 - val_loss: 0.0068
    Epoch 45/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0060 - val_loss: 0.0069
    Epoch 46/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0059 - val_loss: 0.0067
    Epoch 47/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0058 - val_loss: 0.0066
    Epoch 48/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0057 - val_loss: 0.0064
    Epoch 49/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0057 - val_loss: 0.0064
    Epoch 50/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0057 - val_loss: 0.0065
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0056 - val_loss: 0.0062
    Epoch 52/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0056 - val_loss: 0.0062
    Epoch 53/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0055 - val_loss: 0.0062
    Epoch 54/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0055 - val_loss: 0.0061
    Epoch 55/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0055 - val_loss: 0.0060
    Epoch 56/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0054 - val_loss: 0.0061
    Epoch 57/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0054 - val_loss: 0.0060
    Epoch 58/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0053 - val_loss: 0.0060
    Epoch 59/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0053 - val_loss: 0.0059
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0053 - val_loss: 0.0058
    Epoch 61/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0052 - val_loss: 0.0058
    Epoch 62/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0052 - val_loss: 0.0058
    Epoch 63/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0053 - val_loss: 0.0058
    Epoch 64/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0052 - val_loss: 0.0057
    Epoch 65/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0052 - val_loss: 0.0058
    Epoch 66/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0052 - val_loss: 0.0057
    Epoch 67/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0051 - val_loss: 0.0057
    Epoch 68/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0051 - val_loss: 0.0055
    Epoch 69/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0051 - val_loss: 0.0057
    Epoch 70/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0051 - val_loss: 0.0057
    Epoch 71/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0051 - val_loss: 0.0056
    Epoch 72/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0051 - val_loss: 0.0055
    Epoch 73/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0056
    Epoch 74/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0056
    Epoch 75/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0051 - val_loss: 0.0054
    Epoch 76/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0051 - val_loss: 0.0055
    Epoch 77/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0051 - val_loss: 0.0055
    Epoch 78/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0054
    Epoch 79/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0055
    Epoch 80/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0050 - val_loss: 0.0055
    Epoch 81/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0054
    Epoch 82/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0054
    Epoch 83/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0053
    Epoch 84/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0050 - val_loss: 0.0055
    Epoch 85/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0054
    Epoch 86/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0053
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0050 - val_loss: 0.0054
    Epoch 88/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0054
    Epoch 89/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0054
    Epoch 90/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0053
    Epoch 91/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0053
    Epoch 92/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0050 - val_loss: 0.0053
    Epoch 93/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0053
    Epoch 94/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0055
    Epoch 95/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0049 - val_loss: 0.0053
    Epoch 96/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0048 - val_loss: 0.0052
    Epoch 97/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0048 - val_loss: 0.0052
    Epoch 98/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0048 - val_loss: 0.0052
    Epoch 99/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0048 - val_loss: 0.0052
    Epoch 100/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0048 - val_loss: 0.0052
</pre>    


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_69_0.png)
    


### Aktivasyonlu büyük model


```python
model = keras.models.Sequential([
    layers.Dense(units=64, input_shape=(9,), activation='relu'),
    layers.Dense(units=64, input_shape=(9,), activation='relu'),
    layers.Dense(1)
])
```


```python
model.summary()
```
<pre>
    Model: "sequential_16"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_25 (Dense)            (None, 64)                640       
                                                                     
     dense_26 (Dense)            (None, 64)                4160      
                                                                     
     dense_27 (Dense)            (None, 1)                 65        
                                                                     
    =================================================================
    Total params: 4,865
    Trainable params: 4,865
    Non-trainable params: 0
    _________________________________________________________________
</pre>    


```python
model.compile(optimizer='adam', loss='mse')
```


```python
history=model.fit(X_train_scaled, y_train_scaled, epochs=100, validation_data=(X_test_scaled, y_test_scaled))
```
<pre>
    Epoch 1/100
    10/10 [==============================] - 1s 22ms/step - loss: 0.1527 - val_loss: 0.0731
    Epoch 2/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0637 - val_loss: 0.0294
    Epoch 3/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0233 - val_loss: 0.0108
    Epoch 4/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0116 - val_loss: 0.0123
    Epoch 5/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0097 - val_loss: 0.0094
    Epoch 6/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0081 - val_loss: 0.0078
    Epoch 7/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0074 - val_loss: 0.0071
    Epoch 8/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0070 - val_loss: 0.0071
    Epoch 9/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0067 - val_loss: 0.0063
    Epoch 10/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0064 - val_loss: 0.0063
    Epoch 11/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0061 - val_loss: 0.0058
    Epoch 12/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0059 - val_loss: 0.0057
    Epoch 13/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0057 - val_loss: 0.0057
    Epoch 14/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0055 - val_loss: 0.0057
    Epoch 15/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0053 - val_loss: 0.0057
    Epoch 16/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0053 - val_loss: 0.0055
    Epoch 17/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0052 - val_loss: 0.0051
    Epoch 18/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0051 - val_loss: 0.0057
    Epoch 19/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0050 - val_loss: 0.0050
    Epoch 20/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0051 - val_loss: 0.0052
    Epoch 21/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0049 - val_loss: 0.0048
    Epoch 22/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0048 - val_loss: 0.0055
    Epoch 23/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0047 - val_loss: 0.0051
    Epoch 24/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0046 - val_loss: 0.0049
    Epoch 25/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0047 - val_loss: 0.0048
    Epoch 26/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0046 - val_loss: 0.0050
    Epoch 27/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0046 - val_loss: 0.0049
    Epoch 28/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0048 - val_loss: 0.0051
    Epoch 29/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0045 - val_loss: 0.0046
    Epoch 30/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0046 - val_loss: 0.0051
    Epoch 31/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0046 - val_loss: 0.0048
    Epoch 32/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0045 - val_loss: 0.0048
    Epoch 33/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0045 - val_loss: 0.0051
    Epoch 34/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0044 - val_loss: 0.0048
    Epoch 35/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0043 - val_loss: 0.0047
    Epoch 36/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0042 - val_loss: 0.0046
    Epoch 37/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0043 - val_loss: 0.0045
    Epoch 38/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0044
    Epoch 39/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0048
    Epoch 40/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0045
    Epoch 41/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0043 - val_loss: 0.0048
    Epoch 42/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0041 - val_loss: 0.0044
    Epoch 43/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0042 - val_loss: 0.0046
    Epoch 44/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0044
    Epoch 45/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0041 - val_loss: 0.0045
    Epoch 46/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0042 - val_loss: 0.0044
    Epoch 47/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0043
    Epoch 48/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0041 - val_loss: 0.0046
    Epoch 49/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0043
    Epoch 50/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0040 - val_loss: 0.0044
    Epoch 51/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0045
    Epoch 52/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0041 - val_loss: 0.0048
    Epoch 53/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0042 - val_loss: 0.0044
    Epoch 54/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0041 - val_loss: 0.0040
    Epoch 55/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0040 - val_loss: 0.0043
    Epoch 56/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0044
    Epoch 57/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0041
    Epoch 58/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0039 - val_loss: 0.0044
    Epoch 59/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0046
    Epoch 60/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0043
    Epoch 61/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0040
    Epoch 62/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0047
    Epoch 63/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0040
    Epoch 64/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0039 - val_loss: 0.0044
    Epoch 65/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0038 - val_loss: 0.0040
    Epoch 66/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0038 - val_loss: 0.0041
    Epoch 67/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0045
    Epoch 68/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0043
    Epoch 69/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0042
    Epoch 70/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0038 - val_loss: 0.0040
    Epoch 71/100
    10/10 [==============================] - 0s 10ms/step - loss: 0.0039 - val_loss: 0.0050
    Epoch 72/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0044
    Epoch 73/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0039 - val_loss: 0.0039
    Epoch 74/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0042
    Epoch 75/100
    10/10 [==============================] - 0s 11ms/step - loss: 0.0038 - val_loss: 0.0041
    Epoch 76/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0041
    Epoch 77/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0036 - val_loss: 0.0042
    Epoch 78/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0040
    Epoch 79/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0036 - val_loss: 0.0044
    Epoch 80/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0043
    Epoch 81/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0048
    Epoch 82/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0039 - val_loss: 0.0042
    Epoch 83/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0042 - val_loss: 0.0043
    Epoch 84/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0043
    Epoch 85/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0036 - val_loss: 0.0041
    Epoch 86/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0036 - val_loss: 0.0045
    Epoch 87/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0040
    Epoch 88/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0042
    Epoch 89/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0044
    Epoch 90/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0044
    Epoch 91/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0036 - val_loss: 0.0041
    Epoch 92/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0037 - val_loss: 0.0041
    Epoch 93/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0034 - val_loss: 0.0040
    Epoch 94/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0035 - val_loss: 0.0044
    Epoch 95/100
    10/10 [==============================] - 0s 8ms/step - loss: 0.0037 - val_loss: 0.0042
    Epoch 96/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0038 - val_loss: 0.0042
    Epoch 97/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0040 - val_loss: 0.0044
    Epoch 98/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0036 - val_loss: 0.0043
    Epoch 99/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0035 - val_loss: 0.0043
    Epoch 100/100
    10/10 [==============================] - 0s 9ms/step - loss: 0.0036 - val_loss: 0.0039
 </pre>   


```python
plt.plot(history.history['loss'], label='loss')
plt.plot(history.history['val_loss'], label='val_loss')
plt.xlabel('Epoch')
plt.ylabel('Error [MPG]')
plt.legend()
plt.grid(True)
plt.show()
```


    
![png](images/04_output_75_0.png)
    



```python
y_test_predict_scaled=model.predict(X_test_scaled)
```
<pre>
    3/3 [==============================] - 0s 4ms/step
</pre>    


```python
y_pred = scaler_y.inverse_transform(y_test_predict_scaled)
```


```python
y_test[:10]
```



<pre>
    array([26. , 21.6, 36.1, 26. , 27. , 28. , 13. , 26. , 19. , 29. ])
</pre>



```python
y_pred[:10]
```



<pre>
    array([[25.561352],
           [21.317728],
           [34.021828],
           [21.4228  ],
           [27.892326],
           [28.932383],
           [12.169561],
           [29.77778 ],
           [18.302343],
           [30.233294]], dtype=float32)
</pre>