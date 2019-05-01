**Routine Name:**           Conjugate Gradient

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc ConjugateGradient.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the solution to the system of equations by using the conjugate gradient method.

**Input:** A double precision 2D array, a double precision array, ints for the number of rows and columns
in the matrix, double for error tolerance, and an int for max number iterations before quitting.

**Output:** This routine returns a double precision array.

**Usage/Example:**

The coefficient and b matrices are inialized

```c_cpp
const int Row = 3;
const int Col = 3;

  double A[Row][Col] =
  {
    { 4,12,-16 },
    { 12,37,-43 },
    { -16,-43,98 }
  };
  
  double b[Row] = { 60, 201, -108 };
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
  double* Sol;
  Sol = CGa, b, Row, Col, tol, maxit);
```

Results printed

```c_cpp
9
6
3
```


**Implementation/Code:** The following is the code for CG()

```c_cpp
#include <iostream>
#include <LandonLinear>

using namespace std;

double* CG(double **A, double b[], const int r, int c, double tol, int maxit)
{
  if (c != r)
  {
    cout << "Matrix must be square" << endl;
    return 0;
  }

  double* res0 = new double[r];    //residual
  double* res1 = new double[r];
  

  // create return array and temporary array using pointers
  double* X1 = new double[r];

  double* X0 = new double[r];

  //use b as the initial guess
  for (int i = 0; i < r; i++)
  {
    X0[i] = b[i];
  }

  for (int i = 0; i < r; i++)
  {
    res0[i] = b[i];

    for (int j = 0; j < r; j++)
    {
      res0[i] = res0[i] - A[i][j] * X0[j];
    }
  }
  
  double d0 = dot(res0, res0, r);
  double d1 = 10 * tol*tol;
  double* S = new double[r];
  double alpha;
  int k = 0;
  double bd = dot(b, b, r);
  double* p0 = res0;
  double* p1 = new double[r];
  for (int i = 0; i < r; i++)
 
  while (d1 > (tol*tol) && k < maxit)
  {
    S = MatXVec(A, p0, r, c, r);
    alpha = d0 / (dot(p0, S, r));
    X1 = SumVecs(X0, (ScaleVec(p0, alpha)), r);
    res1 = SumVecs(res0, (ScaleVec(S, -alpha)), r);
    d1 = dot(res1, res1, r);
    p1 = SumVecs(res1, (ScaleVec(p0, (d1/d0))), r);
    k++;
    X0 = X1;
    res0 = res1;
    p0 = p1;
    d0 = d1;

  }

  //deallocate memory
  delete[] X0;
  delete[] res0;
  delete[] res1;
  delete[] p0;
  delete[] p1;
  delete[] S;
  S = 0;
  p0 = 0;
  p1 = 0;
  res0 = 0;
  res1 = 0;
  X0 = 0;

  return X1;
}
```

**Last Modified:** April/2019


