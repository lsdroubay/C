**Routine Name:**           Forward Substitution

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc ForSubs.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the solution to a system where the coefficient matrix is lower triangular.

**Input:** A double precision 2D array, a double precision array, an int for the number of rows and columns in the matrix.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 4;
const int Col = 4;

  double A[Row][Col] =
  {
    { 5,0,0,0 },
    { -6,3,0,0 },
    { 1,-2,8,0 },
    { -1,3,2,-2 }
  };

  double b[Row] = { 20, -15, 14, 7 };
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
double* FS;
FS = ForSubs(a, b, Row, Col);
```

Results printed

```c_cpp
4
3
2
1
```

**Implementation/Code:** The following is the code for ForSubs()

```c_cpp
#include <iostream>

using namespace std;

double* ForSubs(double **A, double b[], int r, int c)
{
  if (c != r)
  {
    cout << "Matrix must be square" << endl;
    return 0;
  }

  // create return array using a pointer
  double* X;
  X = new double[r];

  //sum to be used through each row
  double sum;


  //largest/last cell number
  int n = r - 1;

  X[0] = b[0] / A[0][0];

  //Forward Substitution
  for (int i = 1; i <= n; i++)
  {
    sum = b[i];
    for (int j = 0; j < i ; j++)
    {
      sum = sum - (A[i][j] * X[j]);
    }

    X[i] = sum / A[i][i];
  }

  //return array, X
  return X;
}
```
**Last Modified:** March/2019


