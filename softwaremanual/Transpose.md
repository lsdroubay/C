**Routine Name:**           Transpose Matrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc Transpose.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the transpose of a given matrix.

**Input:** A double precision 2D array, an int for the number of rows in the matrix, and an int for columns.

**Output:** This routine returns a double 2D array.

**Usage/Example:**

A double-precision 2D array is initialized

```c_cpp
const int Row = 4;
const int Col = 3;

 double Mat[Row][Col] =
  {
    { 1,2,-1,0 },
    { 0,1,1,-2 },
    { 2,4,1,-3 },
    { 1,-4,-7,-1 }
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
      a[i][j] = Mat[i][j];
    }
  }
```

Initialize double pointer and call function to calculate scaled matrix

```c_cpp
double** TransMat;
TransMat = Transpose(a, Row, Col);
```

Results printed using `cout` and two `for` loops

```c_cpp
1  0  2  1
2  1  4  -4
-1  1  1  -7
0  -2  -3  -1
```

**Implementation/Code:** The following is the code for Transpose()

```c_cpp
#include <iostream>

using namespace std;

double** Transpose(double **a, int row, int col)
{
  // create 2D pointers (so matrix can be returned from the function)
  double** array2D = 0;
  array2D = new double*[col];

  for (int h = 0; h < col; h++)
  {
    array2D[h] = new double[row];
  }

  //Transpose matrix
  for (int i = 0; i < row; i++)
  {
    for (int j = 0; j < col; j++)
    {
      array2D[j][i] = a[i][j];
    }
  }

  //return transposed matrix
  return array2D;
}
```
**Last Modified:** April/2019


