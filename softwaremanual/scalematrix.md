**Routine Name:**           Scale Matrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc ScaleMat.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the scalar multiple of a given matrix.

**Input:** A double precision 2D array, a double precision scalar, an int for the number of rows in the matrix, and an int for columns.

**Output:** This routine returns a double 2D scaled array.

**Usage/Example:**

A double-precision 2D array is initialized

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
```
The scalar is initialized.

```c_cpp
double Scale = 1.50;
```

A pointer to a pointer is made so that a 2D array can be passed to the function. It is set equal to the initialized matrix.

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

Initialize double pointer and call function to calculate scaled matrix

```c_cpp
double** SM;
SM = ScaleMat(s, Scale, Row, Col);
```

Results printed using `cout` and two `for` loops

```c_cpp
1.5  3  4.5
6  7.5  9
10.5  12  13.5
0  4.5  0
```

**Implementation/Code:** The following is the code for l1-norm()

```c_cpp
#include <iostream>

using namespace std;

double l1_norm(double v[])
{
  //initialize to be summed every iteration
  double sum = 0.0;

  //get size of vector
  int n = sizeof(v);

  //sum the absolute value of each vector element
  for (int i = 0; i < n; i++)
  {
    sum = sum + abs(v[i]);
  }

  return sum;
}
```
**Last Modified:** February/2019


