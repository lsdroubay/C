**Routine Name:**           Least Squares - Normal Equation

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc NormalLS.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the solution to a Least Squares problem.

**Input:** A double precision 2D array, a double precision array, an int for the number of rows and columns in the matrix.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 5;
const int Col = 3;

double A[Row][Col] =
  {
    { 1,0,1},
    { 2,3,5 },
    { 5,3,-2 },
    { 3,5,4 },
    {-1,6,3}
  };

  double b[Row] = { 4, -2, 5, -2, 1 };
```

Initialize pointers to pass L and U to the function

```c_cpp
  double **a;
  a = new double *[Row];
  for (int i = 0; i <Row; i++)
    a[i] = new double[Col];


  for (int i = 0; i < Row; i++)
  {
    for (int j = 0; j < Col; j++)
    {
      a[i][j] = A[i][j];
    }
  }
```

Initialize pointer and call function to solve the system

```c_cpp
  double* XX;
  XX = NormLS(a, b, Row, Col);
```

Results printed

```c_cpp
0.347226
0.399004
-0.785917
```

This function utilizes code for [Cholesky Decomposition](https://lsdroubay.github.io/math5610/softwaremanual/Cholesky), [Forward Substitution](https://lsdroubay.github.io/math5610/softwaremanual/ForwardSubstitution), [Back Substitution](https://lsdroubay.github.io/math5610/softwaremanual/BackSubstitution), [Transpose Matrix](https://lsdroubay.github.io/math5610/softwaremanual/Transpose), and [Product of Matrix and Vector](https://lsdroubay.github.io/math5610/softwaremanual/MatXVec).

**Implementation/Code:** The following is the code for LU_Solve()

```c_cpp
#include <iostream>

using namespace std;

double* LU_Solve(double **U, double **L, double b[], int r, int c)
{
  LU_Fac(U, L, r, c);

  //initialize y vector for solving intermediate step
  double* y;
  y = new double[r];

  //initialize x vector for solving final step
  double* X;
  X = new double[r];
  
  //solve with forward substitution
  y = ForSubs(L, b, r, c);

  //now get x with back substitution
  X = BackSubs(U, y, r, c);

  //deleting the new to avoid memory leaks
  delete[] y;
  y = 0;

  //output
  return X;
}
```
**Last Modified:** April/2019


