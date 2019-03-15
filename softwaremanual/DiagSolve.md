**Routine Name:**           Solve Diagonal System

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc DiagSolve.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the solution to a system where the coefficient matrix is diagonal.

**Input:** A double precision 2D array, a double precision array, an int for the number of rows and columns in the matrix.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 4;
const int Col = 4;

double A[Row][Col] =
  {
    { 1.5,0,0,0 },
    { 0,3.6,0,0 },
    { 0,0,8.0,0 },
    { 0,0,0,5.4 }
  };

  double b[Row] = { 3,39.6,96,27 };
```

Initialize a pointer to pass to the function

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

Initialize pointer and call function to solve the diagonal system

```c_cpp
double* DS;
DS = DiagSolve(a, b, Row, Col);
```

Results printed

```c_cpp
2
11
12
5
```

**Implementation/Code:** The following is the code for DiagSolve()

```c_cpp
#include <iostream>

using namespace std;

double* DiagSolve(double **A, double b[], int r, int c)
{
  // create return array using a pointer
  double* X;
  X = new double[r];


  //dividing diagonal A term from correlating value in B
  for (int i = 0; i < r; i++)
  {
      X[i] = b[i] / A[i][i];
    
  }

  //return array, X
  return X;
}
```
**Last Modified:** March/2019


