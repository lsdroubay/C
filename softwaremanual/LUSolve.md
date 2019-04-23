**Routine Name:**           LU Factorization Solve

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc LU_Solve.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the solution to the system of equations by performing LU factorization.

**Input:** A double precision 2D array, a double precision array, an int for the number of rows and columns in the matrix.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 4;
const int Col = 4;

double A[Row][Col] =
  {
    { 1,2,-1,0 },
    { 0,1,1,-2 },
    { 2,4,1,-3 },
    { 1,-4,-7,-1 }
  };

  double b[Row] = { 2, -3, -2, -19 };
```

Initialize pointers to pass L and U to the function

```c_cpp
double **L, **U;

  //A will be replaced with U, so that A doesn't need to be passed
  U = new double *[Row];
  L = new double *[Row];
  for (int i = 0; i < Row; i++)
  {
    U[i] = new double[Col];
    L[i] = new double[Col];
  }

  for (int i = 0; i < Row; i++)
  {
    for (int j = 0; j < Col; j++)
    {
      //set pointer a equal to A
      U[i][j] = A[i][j];

      //initialize L with zeros
      L[i][j] = 0;
    }
  }
```

Initialize pointer and call function to solve the system

```c_cpp
  double* S;
  S = LU_Solve(U, L, b, Row, Col);
```

Results printed

```c_cpp
-1
2
1
3
```

This function utilizes code for [LU Factorization](https://lsdroubay.github.io/math5610/softwaremanual/LUFactorization), [Forward Substitution](https://lsdroubay.github.io/math5610/softwaremanual/ForwardSubstitution), and [Back Substitution](https://lsdroubay.github.io/math5610/softwaremanual/BackSubstitution).

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


