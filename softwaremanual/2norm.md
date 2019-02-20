**Routine Name:**           L2 Norm

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc l2_norm.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the 2-norm of an arbitrary vector will real number entries.

**Input:** A double precision array.

**Output:** This routine returns the 2-norm of the array.

**Usage/Example:**

A double-precision array is initialized

```c_cpp
double Vec[] = { 1, 2, 3, 4 };
```
Call routine to find 2-norm.

```c_cpp
double Norm = l2_norm(Vec);
```

Printing the results yields

```c_cpp
5.47723
```

**Implementation/Code:** The following is the code for l2-norm()

```c_cpp
#include <iostream>

using namespace std;

double l2_norm(double v[])
{
  double sum = 0.0;

  int n = sizeof(v);

  for (int i = 0; i < n; i++)
  {
    sum = sum + (v[i] * v[i]);
  }

  sum = sqrt(sum);

  return sum;
}
```
**Last Modified:** February/2019

