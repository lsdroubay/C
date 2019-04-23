**Routine Name:**           Generate Random SPD Matrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc SPD.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** This routine will generate a random square symmetric positive definite matrix of a given size. That is, the number of rows is input and an (row)x(row) SPD matrix is created.

**Input:** integer for number of rows.

**Output:** This routine returns a n SPD matrix.

**Usage/Example:**

The number of rows is initialized and a pointer made to pass result from function. 

```
  int row = 3;

  double** MM = SPD(row);
```

Printed output from the lines above:
```
0.354997,  0.423476,  0.664448,
0.423476,  1.226575,  1.202300,
0.664448,  1.202300,  1.602518,
```

Using the simple `rand()` function does not create a truly random number. Rerunning the code above produces the exact same matrix. To obtain different results, the routines used to create a value to each cell would need to be modified.
The function creates an SPD matrix by multiply a random matrix by it's transpose. Results can be tested by running a [Cholesky Decomposition](https://lsdroubay.github.io/math5610/softwaremanual/Cholesky), which only works for SPD matrices.
The functions for [Transpose](https://lsdroubay.github.io/math5610/softwaremanual/Transpose) of a matrix and [Matrix Multiplication](https://lsdroubay.github.io/math5610/softwaremanual/MatrixProd) are utilized to create the matrix.

**Implementation/Code:** The following is the code for SPD()

```c_cpp
#include <iostream>

using namespace std;

double** SPD(int r)
{
  // create 2D array using pointers
  double** mat = 0;
  mat = new double*[r];

  //each cell, one by one
  for (int h = 0; h < r; h++)
  {
    mat[h] = new double[r];

    for (int w = 0; w < r; w++)
    {
      // assign random double value to cell, between 0 and 1
      mat[h][w] = (double)rand() / double(RAND_MAX);
    }
  }

  double** TMat = Transpose(mat, r, r);

  double** MM = MatProd(mat, TMat, r, r, r, r);


  // important: clean up memory
  for (int h = 0; h < r; h++)
  {
    delete[] TMat[h];
    delete[] mat[h];
  }
  delete[] TMat;
  delete[] mat;
  TMat = 0;
  mat = 0;
  
  //return matrix
  return MM;
}

```
**Last Modified:** April/2019

