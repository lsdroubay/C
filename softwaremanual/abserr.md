**Routine Name:**           AbsErr

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc AbsErr.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o AbsErr AbsErr.cpp

**Description/Purpose:** Implement a method/routine that computes and returns the absolute error in the approximation of 
a number x by another number y.

**Input:** A double precision value and another that represents an approximation of that value.

**Output:** This routine returns the absolute error between two numbers.

**Usage/Example:**

Two double-precision numbers are initialized

```c_cpp
double real = 5.667;
double approx = 5.5;
```
A pointer array is initialized. It is then given the value of the sums of the two vectors by calling SumVecs.

```c_cpp
float* Z;
Z = ScaleVec(T, S);
```

Using a for-loop to print this vector, G, the following is ouput.

```c_cpp
[20, 15, -125, 5]
```

**Implementation/Code:** The following is the code for ScaleVec()

```c_cpp
#include <iostream>

using namespace std;

float* ScaleVec(float a[], float s)
{
  //
  int VecSize = sizeof(a);

  //Vector to be output
  float* v = a;

  //for-loop to multiply idividual elements of the vector, a, by the scalar, s
  for (int i = 0; i < VecSize; i++)
  {
    v[i] = a[i] * s;
  }

  //return vector that contains the scaled vector
  return v;
}
```
**Last Modified:** January/2019
