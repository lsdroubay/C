**Routine Name:**           RandMatrix

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc RandMatrix.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o RandMatrix RandMatrix.cpp

**Description/Purpose:** This routine will generate a random matrix of a given size. That is, the number of rows and columns are input and the matrix is created by setting each entry in the matrix to a random value between zero and one.

**Input:** integer for number of rows and integer for number of columns.

**Output:** This routine returns a matrix whose cells are each a random floating point integer between 0 and 1.

**Usage/Example:**

The number of rows and columns is input. For example, this code would create a 3x5 matrix. The function is then called using pointers for a float array to create the matrix. The result is output by printing to screen the value of each cell.

```
  // row and col of matrix
  int row = 3;
  int col = 5;

  // call function to create random matrix
  float** my2DArray = RandMatrix(row, col);

  // print contents of the matrix

  for (int h = 0; h < row; h++)
  {
    for (int w = 0; w < col; w++)
    {
      printf("%f,", my2DArray[h][w]);
    }
    printf("\n");
  }
```

Output from the lines above:
```
0.001251,0.563585,0.193304,0.808740,0.585009,
0.479873,0.350291,0.895962,0.822840,0.746605,
0.174108,0.858943,0.710501,0.513535,0.303995,
```

The columns are seperated by a comma. Using the simple `rand()` function does not create a truly random number. Rerunning the code above produces the exact same matrix. To obtain different results, the routines used to create a value to each cell would need to be modified.

**Implementation/Code:** The following is the code for RandMatrix()

```c_cpp
#include <iostream>

using namespace std;

float** RandMatrix(int row, int col)
{
  // create 2D array using pointers
  float** array2D = 0;
  array2D = new float*[row];

  //each cell, one by one
  for (int h = 0; h < row; h++)
  {
    array2D[h] = new float[col];

    for (int w = 0; w < col; w++)
    {
      // assign random float value to cell, between 0 and 1
      array2D[h][w] = (float)rand() / float(RAND_MAX);
    }
  }

  //return matrix
  return array2D;
}

```
**Last Modified:** January/2019

