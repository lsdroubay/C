## Task 1


```
Rows      Gauss time    Jac time
5          3            798
100        2700         224508
700        841766       9.9611e+06
1200       4.26629e+06  3.5095e+07
3000       7.73809e+07  2.15074e+08
```
Using `<chrono>` to time, Jacobi never seems to be faster. The times were getting closer,
leading me to think that for even larger systems, Jacobi would eventually be faster.
