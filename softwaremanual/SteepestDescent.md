**Routine Name:**           Steepest Descent

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc SteepestDescent.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Returns the solution to the system of equations by following steepest descent.

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
    { 26,-1,2 },
    { -1,15,1, },
    { 2,1,38 }
  };

  double b[Row] = { 30, 32, 118 };
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
  Sol = SteepDesc(a, b, Row, Col, tol, maxit);
```

Results printed

```c_cpp
1
2
3
```


**Implementation/Code:** The following is the code for SteepDesc()

```c_cpp
#include <iostream>

using namespace std;

double* SteepDesc(double **A, double b[], const int r, int c, double tol, int maxit)
{
  if (c != r)
  {
    cout << "Matrix must be square" << endl;
    return 0;
  }

  double* res = new double[r];    //residual
  double rw;
  double* q = new double[r];
  double qw;

  double error = 10 * tol;
  double val;
  double alpha;
  int count = 0;

  // create return array and temporary array using pointers
  double* XNew = new double[r];

  double* XOld = new double[r];

  //use b as the initial guess
  for (int i = 0; i < r; i++)
  {
    XOld[i] = b[i];
  }

  for (int i = 0; i < r; i++)
  {
    res[i] = b[i];
    
    for (int j = 0; j < r; j++)
    {
      res[i] = res[i] - A[i][j] * XOld[j];
    }
  }

  while (error > tol && count < maxit)
  {
    count++;

    for (int i = 0; i < r; i++)
    {
      q[i] = 0;
      for (int j = 0; j < r; j++)
      {
        q[i] += A[i][j] * res[j];
      }
    }

    rw = 0;
    qw = 0;

    for (int i = 0; i < r; i++)
    {
      rw += res[i] * res[i];
      qw += res[i] * q[i];
    }

    alpha = rw / qw;

    for (int i = 0; i < r; i++)
    {
      XNew[i] = XOld[i] + (alpha*res[i]);
    }
    
    error = 0;
    for (int i = 0; i < r; i++)
    {
      //error
      val = XNew[i] - XOld[i];
      error += val*val;

      XOld[i] = XNew[i];
    }

    error = sqrt(error);

  }

  //deallocate memory
  delete[] XOld;
  delete[] res;
  delete[] q;
  res = 0;
  q = 0;
  XOld = 0;

  return XNew;
}
```
**Last Modified:** April/2019


