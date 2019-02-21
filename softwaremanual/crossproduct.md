**Routine Name:**           Cross Product

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc crossprod.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the cross product of two vectors, each of length three.

**Input:** Two double precision arrays.

**Output:** This routine returns a double precision array of the cross product.

**Usage/Example:**

Two double-precision arrays are initialized

```c_cpp
double S[3] = { 1, 2, 3 };
double T[3] = { 4, 5, -6 };
```
Initialize pointer and call routine to find cross product.

```c_cpp
double* C;

C = Cross(S, T);
```

Printing the results yields:

```c_cpp
[ -27, 18, -3, ]
```

**Implementation/Code:** The following is the code for Cross()

```c_cpp
#include <iostream>

using namespace std;

double* Cross(double a[], double b[])
{
  //Vector to be output
  double* v = NULL;

  v = new double[3];

  //Formula for cross product
  v[0] = (a[1] * b[2]) - (a[2] * b[1]);
  v[1] = (a[2] * b[0]) - (a[0] * b[2]);
  v[2] = (a[0] * b[1]) - (a[1] * b[0]);

  //return vector that contains the individual sums
  return v;
}
```
**Last Modified:** February/2019


