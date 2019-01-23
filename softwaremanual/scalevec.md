**Routine Name:**           ScaleVec

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc ScaleVec.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o ScaleVec ScaleVec.cpp

**Description/Purpose:** This routine will multiply a vector by a scalar.

**Input:** A floating point vector and a floating point scalar.

**Output:** This routine returns a floating point vector that is the input vector multiplied by the input scalar.

**Usage/Example:**

A single-precision float array and scalar are assigned and given values. A constant value integer is assigned a value that will be 
the length of the input and output vectors.

```c_cpp
const int Asize = 4;
float T[Asize] = { 4, 3, -25, 1 };
float S = 5.0;
```
A pointer array is initialized. It is then given the value of the sums of the two vectors by calling SumVecs.
Output from the lines above:

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

  //for-loop to sum individual elements of the two vectors, a and b, at index i
  for (int i = 0; i < VecSize; i++)
  {
    v[i] = a[i] * s;
  }

  //return vector that contains the individual sums
  return v;
}
```
**Last Modified:** January/2019
