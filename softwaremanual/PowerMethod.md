**Routine Name:**           Power Method

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc PowerMethod.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the largest eigenvalue of a given matrix.

**Input:** A double precision 2D array, a double precision array initial eigenvector guess, ints for the number of rows and columns
in the matrix, double for error tolerance, and an int for max number iterations before quitting.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The matrix and initial guess, v0, are initialized

```c_cpp
const int Row = 4;
const int Col = 4;

  double A[Row][Col] =
  {
    { 17,1,3,-1 },
    { 1,25,4,8 },
    { 3,4,12,6 },
    { -1,8,6,20 }

  };
  
  double v0[Row] = { 10, 10, 10, 10 };
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

Initialize error tolerance and max number of iterations
```c_cpp
  int maxit = 100;
  double tol = 10e-6;
```

Initialize pointer and call function to solve the system

```c_cpp
  double Eig1 = Power(a, v0, Row, Col, tol, maxit);
```

Results printed

```c_cpp
33.1659
```


**Implementation/Code:** The following is the code for Power()

```c_cpp
#include <iostream>
#include <LandonLinear>

using namespace std;

double Power(double **A, double v0[], const int r, int c, double tol, int maxit)
{
  if (c != r)
  {
    cout << "Matrix must be square" << endl;
    return 0;
  }

  //initialize values
  double* v1 = new double[r];
  double err = 10 * tol;
  int k = 0;
  double y_norm;
  double eig0 = 0;
  double eig1;
  double* y = MatXVec(A, v0, r, c, r);

  while (err > tol && k < maxit)
  {
    k++;
    y_norm = l2_norm(y);
    v1 = ScaleVec(y, (1 / y_norm));
    y = MatXVec(A, v1, r, c, r);
    eig1 = dot(v1, y, r);
    err = abs(eig1 - eig0);
    eig0 = eig1;
  }

  //deallocate memory
  delete[] y;
  delete[] v1;
  v1 = 0;
  y = 0;


  return eig1;
}
```

**Last Modified:** April/2019


