**Routine Name:**           Symmetric Diagonally Dominant Matrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc SymDiagDom.cpp

will produce an executable **./a.exe** than can be executed.

**Description/Purpose:** This routine will generate a symmetric diagonally dominant square matrix of random values for a given size. That is, the number of rows or columns is input and the matrix is created by where each entry in the diagonal of a matrix is larger than the sum of the rest of the entries in the row.

**Input:** integer for number of matrix rows (and columns, since it is a square matrix)

**Output:** This routine returns a symmetric matrix whose cells are diagonally dominant and are a random floating point value.

**Usage/Example:**

The number of rows is initialized. The function is then called using pointers for a 2D array to create the matrix that is a square matrix, the size given. 

```
  int row = 3;

  double** SD = SymDiagDom(row);
```

The result is output by printing to screen the value of each cell.
```
11.756890,  0.563585,  0.193304,
0.563585,  30.148595,  0.585009,
0.193304,  0.585009,  26.778314,
```

The columns are seperated by a comma. 
Using the simple `rand()` function does not create a truly random number. Rerunning the code above produces the exact same matrix. To obtain different results, the routines used to create a random value to each cell would need to be modified.

**Implementation/Code:** The following is the code for SymDiagDom()

```c_cpp
#include <iostream>

using namespace std;

double** SymDiagDom(int r)
{
  // create 2D array using pointers
  double** mat = 0;
  mat = new double*[r];

  // create a column for each row
  for (int h = 0; h < r; h++)
  {
    mat[h] = new double[r];
  }

  //each cell above the diagonal, one by one
  for (int h = 0; h < r; h++)
  {
    for (int w = h; w < r; w++)
    {
      // assign random double value to cell, between 0 and 1
      mat[h][w] = (double)rand() / double(RAND_MAX);

      //assign same value on other side of diagonal to make symmetric
      mat[w][h] = mat[h][w];
    }
  }



  //create larger diagonal terms

  double sum;

  // sum the absolute values of the row and create a random number that is larger
  for (int i = 0; i < r; i++)
  {
    sum = 0;

    for (int j = 0; j < r; j++)
    {
      if (j != i)
      {
        sum = sum + abs(mat[i][j]);
      }
    }
    mat[i][i] = (rand() / 1000) + sum;
  }

  //return matrix
  return mat;
}

```
**Last Modified:** March/2019


