**Routine Name:**           Matrix Row Reduction

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc RowRed.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Performs Gauss Row Reduction on given matrix.

**Input:** A double precision 2D array, an int for the number of rows in the matrix, and an int for columns.

**Output:** A new matrix is not output; instead, the original matrix input is transformed into an upper triangular matrix.

**Usage/Example:**

A double-precision 2D array is initialized

```c_cpp
const int Row = 4;
const int Col = 4;

  double A[Row][Col] =
  {
    { 1,2,-3,-1 },
    { 0,-3,2,6 },
    { -3,-1,3,1 },
    { 2,3,2,-1 }
  };
```

A pointer to a pointer is made so that a 2D array can be passed to the function. It is set equal to the initialized matrix.

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

Call function to perform row reduction on matrix

```c_cpp
RowRed(a, Row, Col);
```

Transformed matrix printed using `cout` and two `for` loops gives:

```c_cpp
1  2  -3  -1
0  -3  2  6
0  0  -2.66667  8
0  0  0  21
```

**Implementation/Code:** The following is the code for RowRed()

```c_cpp
#include <iostream>

using namespace std;

void RowRed(double **A, int r, int c)
{

  //temp to be used through each row
  double temp;

  //Factor to multiply the row above
  double fac;

  for (int k = 0; k < c - 1; k++)
  {

    for (int i = k + 1; i < r; i++)
    {
      fac = A[i][k] / A[k][k];

      for (int j = k; j < c; j++)
      {
        temp = A[i][j];
        A[i][j] = temp - (fac*A[k][j]);
      }   
    }
  }
  return ;
}
```
**Last Modified:** March/2019


