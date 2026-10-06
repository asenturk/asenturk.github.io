# EEM-241 İleri Düzey Programlama

## 2024-2025 Güz Dönemi


### Ders 14 - Raspberry Pi GPIO Programlama


Raspberry Pi GPIO simulator sayfası:   
[https://create.withcode.uk/python/A3](https://create.withcode.uk/python/A3)



```python
import RPi.GPIO as GPIO
import time

# setup pins
GPIO.setmode(GPIO.BOARD)
GPIO.setup(21, GPIO.OUT)

while True:
  GPIO.output(21, GPIO.HIGH)
  time.sleep(1)
  GPIO.output(21, GPIO.LOW)
  time.sleep(1)
```  



```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BOARD)
pinler=[3,5,7,11,13,15]
for pin in pinler:
  GPIO.setup(pin, GPIO.OUT)

while True:
  for pin in pinler:
    GPIO.output(pin, GPIO.HIGH)
    time.sleep(1)
    GPIO.output(pin, GPIO.LOW)
    time.sleep(1)
```  



```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BOARD)
pinler=[3,5,7,11,13,15]
for pin in pinler:
  GPIO.setup(pin, GPIO.OUT)

while True:
  for pin in pinler:
    GPIO.output(pin, GPIO.HIGH)
    time.sleep(0.5)
    GPIO.output(pin, GPIO.LOW)
```  


```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BOARD)
pinler=[3,5,7,11,13,15]
for pin in pinler:
  GPIO.setup(pin, GPIO.OUT)

while True:
  for pin in pinler:
    GPIO.output(pin, GPIO.HIGH)
    time.sleep(0.5)
    GPIO.output(pin, GPIO.LOW)

  for pin in pinler[-2:0:-1]:
    GPIO.output(pin, GPIO.HIGH)
    time.sleep(0.5)
    GPIO.output(pin, GPIO.LOW)
```    

```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BOARD)
pinler=[3,5,7,11,13,15]
for pin in pinler:
  GPIO.setup(pin, GPIO.OUT)
GPIO.setup(12, GPIO.IN)

while True:
  if GPIO.input(12)==GPIO.HIGH:
    for pin in pinler:
      GPIO.output(pin, GPIO.HIGH)
      time.sleep(0.5)
      GPIO.output(pin, GPIO.LOW)
  else:
    for pin in pinler[::-1]:
      GPIO.output(pin, GPIO.HIGH)
      time.sleep(0.5)
      GPIO.output(pin, GPIO.LOW)
```    
