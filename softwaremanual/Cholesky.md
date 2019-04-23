**Routine Name:**           Cholesky Decomposition

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc Cholesky.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the R matrix for which G = R^T * R.

**Input:** A double precision 2D array,
and ints for the number of rows and columns in the matrix.

**Output:** This routine technically does not return anything but changes the passed input matrix.

**Usage/Example:**

The original matrix is initialized

```c_cpp
const int Row = 3;
const int Col = 3;

 double A[row][col] =
  {
    { 4,12,-16 },
    { 12,37,-43 },
    { -16,-43,98 }

  };
```

A 2D pointer is created to pass to the function; initialized with original matrix

```c_cpp
double **CholMat;
  CholMat = new double *[row];
  for (int i = 0; i < row; i++)
    CholMat[i] = new double[col];

  for (int i = 0; i < row; i++)
  {
    for (int j = 0; j < col; j++)
    {
      CholMat[i][j] = A[i][j];
    }
  }
```

Call void function to decompose matrix into lower triangular matrix (R^T);
To get R, one would just use [Transpose](https://lsdroubay.github.io/math5610/softwaremanual/Transpose) function.

```c_cpp
  Chol(CholMat, row, col);
```

Results printed

```c_cpp
2    0    0
6    1    0
-8    5    3
```

**Implementation/Code:** The following is the code for Chol()

```c_cpp
#include <iostream>

using namespace std;

void Chol(double** a, int r, int c)
{
  if (c != r)
  {
    cout << "Matrix must be square" << endl;
    return;
  }

  for (int k = 0; k < r - 1; k++)
  {
    a[k][k] = sqrt(a[k][k]);

    for (int i = k + 1; i < r; i++)
    {
      a[i][k] = a[i][k] / a[k][k];
    }
    for (int j = k + 1; j < r; j++)
    {
      for (int i = j; i < r; i++)
      {
        a[i][j] = a[i][j] - (a[i][k] * a[j][k]);
      }
    }

  }

  a[r - 1][r - 1] = sqrt(a[r - 1][r - 1]);

  //set rest to zero
  for (int i = 0; i < r; i++)
  {
    for (int j = i + 1; j < r; j++)
    {
      a[i][j] = 0;
    }
  }

}
```
**Last Modified:** April/2019


