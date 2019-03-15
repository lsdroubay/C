**Routine Name:**           Marix Multiplication

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc MatProd.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the product of two matrices with an equal inner dimension.

**Input:** Two 2D double precision arrays and integers for the number of rows and columns of each

**Output:** This routine returns a 2D double precision array.

**Usage/Example:**

Two double-precision arrays, S and T, are initialized

```c_cpp
const int SRow = 4;
const int SCol = 3;
const int TRow = 3;
const int TCol = 2;

  double S[SRow][SCol] =
  {
    { 1,2,3 },
    { 4,5,6 },
    { 7,8,9 },
    { 0,3,0 }
  };
  double T[TRow][TCol] =
  {
    { 2,3 },
    { 5,0 },
    { 7,10 }
  };
```
Create  2D pointers to the initialized matrices

```c_cpp
double **s;
  s = new double *[SRow];
  for (int i = 0; i <SRow; i++)
    s[i] = new double[SCol];

  double **t;
  t = new double *[TRow];
  for (int i = 0; i <TRow; i++)
    t[i] = new double[TCol];

  for (int i = 0; i < SRow; i++)
  {
    for (int j = 0; j < SCol; j++)
    {
      s[i][j] = S[i][j];
    }
  }
  
  for (int i = 0; i < TRow; i++)
  {
    for (int j = 0; j < TCol; j++)
    {
      t[i][j] = T[i][j];
    }
  }
```
Call routine to find product of two matrices.

```c_cpp
double** MM;
  MM = MatProd(s, t, SRow, SCol, TRow, TCol);
```

Printing the results yields

```c_cpp
33   33
75   72
117   111
15   0
```

**Implementation/Code:** The following is the code for MatProd()

```c_cpp
#include <iostream>

using namespace std;

double** MatProd(double **a, double **b, int sr, int sc, int tr, int tc)
{
  // create 2D array using pointers
  double** Mat;
  Mat = new double*[sr];

  for (int h = 0; h < sr; h++)
  {
    Mat[h] = new double[tc];
  }

  double sum;

  //going through each column of b and multiplying by the row of a
  for (int i = 0; i < sr; i++)
  {
    for (int j = 0; j < tc; j++)
    {
      sum = 0;
      for (int k = 0; k < sc; k++)
      {
        sum += a[i][k] * b[k][j];
      }
      Mat[i][j] = sum;
    }
  }
  

  //return matrix
  return Mat;
}
```
**Last Modified:** March/2019

