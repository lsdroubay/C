**Routine Name:**           L1 Norm

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc l1_norm.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the 1-norm of an arbitrary vector will real number entries.

**Input:** A double precision array.

**Output:** This routine returns a double, the 1-norm of the array.

**Usage/Example:**

A double-precision array is initialized

```c_cpp
double Vec[] = { 1, 2, 3, 4 };
```
Call routine to find 1-norm.

```c_cpp
double Norm = l1_norm(Vec);
```

Printing the results yields

```c_cpp
10
```

**Implementation/Code:** The following is the code for l1-norm()

```c_cpp
#include <iostream>

using namespace std;

double l1_norm(double v[])
{
  //initialize to be summed every iteration
  double sum = 0.0;

  //get size of vector
  int n = sizeof(v);

  //sum the absolute value of each vector element
  for (int i = 0; i < n; i++)
  {
    sum = sum + abs(v[i]);
  }

  return sum;
}
```
**Last Modified:** February/2019

