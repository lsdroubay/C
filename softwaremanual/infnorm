**Routine Name:**           Infinity Norm

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc inf_norm.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the infinity norm of an arbitrary vector will real number entries.

**Input:** A double precision array.

**Output:** This routine returns a double precision value of the infinity norm of the array.

**Usage/Example:**

A double-precision array is initialized

```c_cpp
double Vec[] = { 1, 2, 3, 4 };
```
Call routine to find 1-norm.

```c_cpp
double Norm = inf_norm(Vec);
```

Printing the results yields

```c_cpp
4
```

**Implementation/Code:** The following is the code for inf_norm()

```c_cpp
#include <iostream>

using namespace std;

double inf_norm(double v[])
{
  //initialize to zero to ensure iterations can start
  double max = 0.0;

  //initialize a double to be temporary placeholder for each iteration
  double temp;

  //get size of vector
  int n = sizeof(v);

  //check each value to see if it is the max
  for (int i = 0; i < n; i++)
  {
    temp = abs(v[i]);

    //if the value is greater than the current max, set as new max
    if (temp > max)
    {
      max = temp;
    }
  }

  return max;
}
```
**Last Modified:** February/2019

