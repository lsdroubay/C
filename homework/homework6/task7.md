## Task 7

[Gauss_Seidel](https://lsdroubay.github.io/math5610/softwaremanual/GauessSeidel) and [Jacobi iteration](https://lsdroubay.github.io/math5610/softwaremanual/JacobiIteration) methods are compared
for a max tolerance of 10e-5. {DiagDomMat](https://lsdroubay.github.io/math5610/softwaremanual/DiagonalMatrix) was used to create a random diagonally dominant A matrix. A is multiplied by a known x
to get a b. x is then solved and compared using the two methods. The number of iterations for each system are output.

```
Rows      GauSei iter    Jac iter
5      5        6
100      10        39
700      12        224
1200      12        395
3000      13        942
```
