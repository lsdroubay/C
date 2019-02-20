**Routine Name:**           L2 Error

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc l2_error.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the error of two vectors of equal size using the 2-norm.

**Input:** Two double precision arrays and an int for their size.

**Output:** This routine returns a double precision error value.

**Usage/Example:**

Two double-precision arrays are initialized

```c_cpp
const int Asize = 5;

double S[Asize] = { 1, 2, 7, 4, 1 };
double T[Asize] = { 4, 2, -2, 3, 2 };
```
Call routine to find error.

```c_cpp
double E;
E = l2error(S, T, Asize);
```

Printing the results yields

```c_cpp
9.59166
```

**Implementation/Code:** The following is the code for l2_error()

```c_cpp
#include <iostream>

using namespace std;

double l2error(double a[], double b[], int Size)
{
  //temp variable to replace b with error array
  double temp;

  //sum variable used to calculate L2 Norm
  double sum = 0;

  //for-loop to take abs error of corresponding elements of the two vectors, a and b, at index i
  //replace b vector with error values
  for (int i = 0; i < Size; i++)
  {
    temp = abs(a[i] - b[i]);
    b[i] = temp;
    sum = sum + (b[i] * b[i]);
  }

  sum = sqrt(sum);

  //return the sum (L2 Norm)
  return sum;

}
```
**Last Modified:** February/2019

