# DSP hw1
 
| task | number | page (pdf) | status |
|:---:|:---:|:---:|---|
| example | 2.9 | 16 | done |
| example | 2.45 | 31 | done |
| example | 3.16 | 61 | done |
| example | 4.5 | 74 | done |
| example | 5.6 | 92 | done |
| exercise | 2.35 | 35 | done |
| exercise | 3.23 | 50 | pending |
| exercise | 3.5 | 41 | pending |
| exercise | 4.20 | 80 | pending |
| exercise | 5.12 | 86 | pending |
| exercise | 6.15 | 115 | pending |
---
## Examples

### 2.9
```python
help(np.math) # Make sure to import numpy library as np
```

### 2.45
```python
while index <= n:
    s = s + index
    index = index + 1
    # Typecasting an integer to string: str(x)
    print('The sum is ', str(s))
```

### 3.16
copy the following on console :
```python
np.array([3.4*10**38, 3.5*10**38], dtype = 'f')
```
output:
```python
array([3.4e+38,     inf], dtype=float32)
```

### 4.5
```python
import myLib

A = 1
fs = 100
t = myLib.time(-100,1/fs,1) # time vector

x = myLib.sine(1,0,t)

plt.subplot(2,1,1)
plt(t, x)
plt.axis([-5, 5, -.5, 1.5])
plt.title('Amplitude of the Impulse function')
plt.xlabel('Times (s)')
plt.ylabel('Amplitude')
X = np.fft(x)
Z = np.abs(X)
N = np.ceil(len(Z)/2)
Z = Z(1,N)

f = np.arrange(0, fs/2/(N-1), fs/2)
plt.subplot(2, 1, 2)
plt(f, Z)
plt.title('Magnitude spectrum - single sided')
plt.xlabel('Frequency (Hz)')
plt.ylabel('Magnitude')
```

### 5.6
```python
import numpy as np
import time
import random

errAccepted = 10**-10
maxPower = 11
powerArray = np.arange(1, maxPower)

tocArr = [0,0]

for index in powerArray:
    N = 2**index
    x = random.randrange(1, N)
    y = random.randrange(1, N)
    tic = time.time()
    z1 = np.convolve(x,y) # normal convolution
    toc = time.time()
    tocArr[0] = toc
    
    # faster version
    X = np.fft.fft([x, np.zeros(1, N)]) # transfer to frequency domain
    Y = np.fft.fft([y, np.zeros(1, N)])
    Z = X*Y
    tic = time.time()
    
    z2 = np.fft.ifft(Z) # transfer to time domain
    toc = time.time()
    tocArr[1] = toc
    z2= np.arange(1, 2*(N-1))
    
    if ~all(np.abs(z1 - z2) < errAccepted):
        print('different results')
```
---
## Exercises

### 2.35
```python
x = []
x = [math.sqrt(n + 1) for n in range(100)]
x[1] = 100
print(x)
```
- `x[99]` and `x[100]` are not really equal, they are approximately close
```python
x[99]  = 9.9498743710662
x[100] = 10.0
```
