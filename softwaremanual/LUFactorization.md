**Routine Name:**           LU Factorization

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc LU_Fac.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the two LU factored matrices, one upper triangular one lower.

**Input:** Two double precision 2D arrays (one is the original matrix while the other is an empty one to be filled),
and ints for the number of rows and columns in the matrix.

**Output:** This routine technically does not return anything but changes the two input matrices.

**Usage/Example:**

The original matrix is initialized

```c_cpp
const int Row = 4;
const int Col = 4;

 double A[Row][Col] =
  {
    { 2, 4, -4, 0 },
    { 1, 5, -5, -3 },
    { 2, 3, 1, 3 },
    { 1, 4, -2, 2 }
  };
```

Two 2D pointers are created for L and U to pass to the function. 
U is initially set equal to A, so that only two matrices need to be passed instead of three.
L is intialized with zeros.

```c_cpp
for (int i = 0; i < Row; i++)
  {
    U = new double *[Row];
    L = new double *[Row];
    
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

Call void function to factor matrix into L and U matrices

```c_cpp
  LU_Fac(U, L, Row, Col);
```

Results printed (U matrix then L)

```c_cpp
2  4  -4  0
0  3  -3  -3
0  0  4  2
0  0  0  3

1  0  0  0
0.5  1  0  0
1  -0.333333  1  0
0.5  0.666667  0.5  1
```
This code does not have to return two matrices. If it is desired to have the LU factorization
in a single matrix, see the 30th line of the following code and remove the comment slashes.

**Implementation/Code:** The following is the code for LU_Fac()

```c_cpp
#include <iostream>

using namespace std;

void LU_Fac(double **A, double **L, int r, int c)
{
  if (r != c)
  {
    cout << "A must be a square matrix\n";
    return;
  }

  for (int i = 0; i < r; i++)
  {
    L[i][i] = 1;
  }

  for (int k = 0; k < c - 1; k++)
  {

    for (int i = k + 1; i < r; i++)
    {
      L[i][k] = A[i][k] / A[k][k];

      for (int j = k; j < c; j++)
      {
        A[i][j] = A[i][j] - (L[i][k]*A[k][j]);
      }

      //if you want to store L and U in one matrix
      //A[i][k] = L[i][k];
    }

  }
  return;
}
```
**Last Modified:** April/2019


