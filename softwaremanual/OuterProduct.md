**Routine Name:**           Outer Product

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc OutProd.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the outer product of two vectors.

**Input:** Two double precision arrays and integers representing the length of each vector.

**Output:** This routine returns a 2D double precision array (matrix) of the outer product.

**Usage/Example:**

Two double-precision arrays are initialized

```c_cpp
const int Asize = 3;
const int Bsize = 4;

double S[Asize] = { 3, 4, 1 };
double T[Bsize] = { 3, 7, 5, 6 };
```
Initialize pointer and call routine to find outer product.

```c_cpp
 double** G;
 G = OutProd(S, T, Asize, Bsize);
```

Printing the results yields:

```c_cpp
9  21  15  18
12  28  20  24
3  7  5  6
```

**Implementation/Code:** The following is the code for OutProd()

```c_cpp
#include <iostream>

using namespace std;

double** OutProd(double a[], double b[], int s1, int s2)
{
  // create 2D array using pointers
  double** Mat;
  Mat = new double*[s1];

  for (int h = 0; h < s1; h++)
  {
    Mat[h] = new double[s2];
  }


  //multiply row of a by each column of b
  
  for (int i = 0; i < s1; i++)
  {
    for (int j = 0; j < s2; j++)
    {
      Mat[i][j] = a[i] * b[j];
    }
  }

  //return the Matrix
  return Mat;

}
```
**Last Modified:** March/2019


