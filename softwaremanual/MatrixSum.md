**Routine Name:**           Marix Sum

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc MatSum.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the sum of two matrices of equal dimension.

**Input:** Two 2D double precision arrays and integers for the number of rows and columns

**Output:** This routine returns a 2D double precision array.

**Usage/Example:**

Two double-precision arrays, S and T, are initialized

```c_cpp
const int Row = 4;
const int Col = 3;

  double S[Row][Col] =
  {
    { 1,2,3 },
    { 4,5,6 },
    { 7,8,9 },
    { 0,3,0 }
  };
  double T[Row][Col] =
  {
    { 9,8,7 },
    { 6,5,4 },
    { 3,2,1},
    { 10,7,10 }
  };
```
Create  2D pointers to the initialized matrices

```c_cpp
  double **s;
  s = new double *[Row];
  for (int i = 0; i <Row; i++)
    s[i] = new double[Col];

  double **t;
  t = new double *[Row];
  for (int i = 0; i <Row; i++)
    t[i] = new double[Col];

  for (int i = 0; i < Row; i++)
  {
    for (int j = 0; j < Col; j++)
    {
      s[i][j] = S[i][j];
    }
  }

  for (int i = 0; i < Row; i++)
  {
    for (int j = 0; j < Col; j++)
    {
      t[i][j] = T[i][j];
    }
  }
```
Call routine to find product of two matrices.

```c_cpp
double** MS;
MS = MatSum(s, t, Row, Col);
```

Printing the results yields

```c_cpp
10  10  10
10  10  10
10  10  10
10  10  10
```

**Implementation/Code:** The following is the code for MatProd()

```c_cpp
#include <iostream>

using namespace std;

double** MatSum(double **a, double **b, int r, int c)
{
  // create 2D array using pointers
  double** Mat;
  Mat = new double*[r];

  for (int h = 0; h < r; h++)
  {
    Mat[h] = new double[c];
  }
  
  //going through each cell of a and summing with corellating cell of b
  for (int i = 0; i < r; i++)
  {
    for (int j = 0; j < c; j++)
    {
      Mat[i][j] = a[i][j] + b[i][j];
    }
  }

  //return matrix
  return Mat;
}
```
**Last Modified:** March/2019

