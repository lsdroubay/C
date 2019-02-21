**Routine Name:**           SymMatrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc SymMat.cpp

will produce an executable **./a.exe** than can be executed.

**Description/Purpose:** This routine will generate a symmetric matrix of random values for a given size. That is, the number of rows and columns are input and the matrix is created by setting each entry in the matrix to a random value between zero and one.

**Input:** integer for number of matrix rows (and columns, since it is a square matrix)

**Output:** This routine returns a matrix whose cells are symmetric and are a random floating point value between 0 and 1.

**Usage/Example:**

The number of rows is initialized. The function is then called using pointers for a 2D array to create the matrix that is a square matrix, the size given. 

```
  int row = 4;

  float** myMatrix = SymMat(row);
```

The result is output by printing to screen the value of each cell.
```
0.001251,0.563585,0.193304,0.808740,
0.563585,0.585009,0.479873,0.350291,
0.193304,0.479873,0.895962,0.822840,
0.808740,0.350291,0.822840,0.746605,
```

The columns are seperated by a comma. Using the simple `rand()` function does not create a truly random number. Rerunning the code above produces the exact same matrix. To obtain different results, the routines used to create a random value to each cell would need to be modified.

**Implementation/Code:** The following is the code for RandMatrix()

```c_cpp
#include <iostream>

using namespace std;

float** SymMat(int row)
{
  // create 2D array using pointers
  float** matrix = 0;
  matrix = new float*[row];

 // create a column for each row
  for (int h = 0; h < row; h++)
  {
    matrix[h] = new float[row];
  }

  //each cell above the diagonal, one by one
  for (int h = 0; h < row; h++)
  {
    for (int w = h; w < row; w++)
    {
      // assign random float value to cell, between 0 and 1
      matrix[h][w] = (float)rand() / float(RAND_MAX);

      //assign same value on other side of diagonal to make symmetric
      matrix[w][h] = matrix[h][w];
    }
  }

  //return matrix
  return matrix;
}

```
**Last Modified:** February/2019


