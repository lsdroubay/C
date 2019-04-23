The software manual for [Cholesky Decomposition](https://lsdroubay.github.io/math5610/softwaremanual/Cholesky) also documents the results from a simple 3x3 matrix.
Using the [SPD](https://lsdroubay.github.io/math5610/softwaremanual/SPDmat) program to create a 300 x 300 SPD matrix, 
the Cholesky Decomposition was performed. 

```c_cpp
int row = 300;

double** MM = SPD(row);

Chol(MM, row, row);
```
Results:
