**Routine Name:**           Least Squares - Normal Equation

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc NormalLS.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the solution to a Least Squares problem.

**Input:** A double precision 2D array, a double precision array, an int for the number of rows and columns in the matrix.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 5;
const int Col = 3;

double A[Row][Col] =
  {
    { 1,0,1},
    { 2,3,5 },
    { 5,3,-2 },
    { 3,5,4 },
    {-1,6,3}
  };

  double b[Row] = { 4, -2, 5, -2, 1 };
```

Initialize pointers to pass matrix to the function

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

Initialize pointer and call function to solve the LS problem

```c_cpp
  double* XX;
  XX = NormLS(a, b, Row, Col);
```

Results printed

```c_cpp
0.347226
0.399004
-0.785917
```

This function utilizes code for [Cholesky Decomposition](https://lsdroubay.github.io/math5610/softwaremanual/Cholesky), [Forward Substitution](https://lsdroubay.github.io/math5610/softwaremanual/ForwardSubstitution), [Back Substitution](https://lsdroubay.github.io/math5610/softwaremanual/BackSubstitution), [Transpose Matrix](https://lsdroubay.github.io/math5610/softwaremanual/Transpose), and [Product of Matrix and Vector](https://lsdroubay.github.io/math5610/softwaremanual/MatXVec).

**Implementation/Code:** The following is the code for LU_Solve()

```c_cpp
#include <iostream>
#include <LandonLinear>

using namespace std;

double* NormLS(double **A, double b[], int r, int c)
{
  //B= A^T * A
  double** AT = Transpose(A, r, c);

  double** B = MatProd(AT, A, c, r, r, c);
  
  //y = A^T * b
  double* y = MatXVec(AT, b, c, r, r);
  
  //Cholesky Decomp of B
  Chol(B, c, c);

  double** BT = Transpose(B, c,c);

  //Solve Bz = y
  double* z = ForSubs(B, y, c, c);

  //Solve B^T * x = z
  double* X = BackSubs(BT, z, c, c);

  
  // important: clean up memory
    for (int h = 0; h < c; h++)
    {
      delete[] AT[h];
      delete[] B[h];
      delete[] BT[h];
    }
  delete[] AT;
  delete[] B;
  delete[] BT;
  delete[] y;
  delete[] z;
  AT = 0;
  B = 0;
  BT = 0;
  y = 0;
  z = 0;

  //return array, X
  return X;
}
```
**Last Modified:** April/2019


