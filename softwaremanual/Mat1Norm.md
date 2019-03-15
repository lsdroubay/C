**Routine Name:**           Matrix 1-Norm

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc Matrix1Norm.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the 1-norm of an arbitrary matrix with real number entries.

**Input:** A 2D double precision array and integers for the number of rows and columns

**Output:** This routine returns a double, the 1-norm of the matrix.

**Usage/Example:**

A double-precision array is initialized

```c_cpp
double S[Row][Col] =
  {
    { 1,2,3 },
    { 4,5,6 },
    { 7,8,9 },
    { 0,3,0 }
  };
```
Create a 2D pointer to the initialized matrix

```c_cpp
double **s;
  s = new double *[Row];
  for (int i = 0; i <Row; i++)
    s[i] = new double[Col];


  for (int i = 0; i < Row; i++)
  {
    for (int j = 0; j < Col; j++)
    {
      s[i][j] = S[i][j];
    }
  }
```
Call routine to find 1-norm.

```c_cpp
double norm;
  norm = Mat1Norm(s, Row, Col);
```

Printing the results yields

```c_cpp
18
```

**Implementation/Code:** The following is the code for Mat1Norm()

```c_cpp
#include <iostream>

using namespace std;

double Mat1Norm(double **a, int r, int c)
{ 

  //sum of row and temp max value
  double sum;
  double max = 0;

  //summing each row of matrix and comparing to temporary max value
  for (int j = 0; j < c; j++)
  {
    sum = 0;

    for (int i = 0; i < r; i++)
    {
      sum = sum + a[i][j];
    }

    if (sum > max)
    {
      max = sum;
    }

  }

  //return matrix
  return max;
}
```
**Last Modified:** March/2019

