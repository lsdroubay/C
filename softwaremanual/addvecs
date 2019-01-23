**Routine Name:**           SumVecs

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc SumVecs.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o SumVecs SumVecs.cpp

**Description/Purpose:** This routine will add two vectors of the same length.

**Input:** Two floating point vectors and the size of the new vector.

**Output:** This routine returns a floating point vector that is the sum of the two input vectors. The size that is input 
will determine the size of the output matrix.

**Usage/Example:**

Two single-precision float arrays are assigned and given values. A constant value integer is assigned a value that will be 
the length of the output vector.

'''c_cpp
const int Asize = 4;
float S[Asize] = { 1, 2, 33, 4 };
float T[Asize] = { 4, 3, -28, 1 };
'''
A pointer array is initialized. It is then given the value of the sums of the two vectors by calling SumVecs.
Output from the lines above:

'''c_cpp
float* G;
G=SumVecs(S,T,Asize);
'''

Using a for-loop to print this vector, G, the following is ouput.

'''c_cpp
[5, 5, 5, 5]
'''

**Implementation/Code:** The following is the code for SumVecs()

```c_cpp
#include <iostream>

using namespace std;

float* SumVecs(float a[], float b[], int VecSize)
{
  //Vector to be output
  float* v = a;

  //for-loop to sum individual elements of the two vectors, a and b, at index i
  for (int i = 0; i < VecSize; i++)
  {
    v[i] = a[i] + b[i];
  }

  //return vector that contains the individual sums
  return v;
}
```
**Last Modified:** January/2019
