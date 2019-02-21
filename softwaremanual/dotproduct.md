**Routine Name:**           Dot Product

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc Dot.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the dot product of two vectors of equal size.

**Input:** Two double precision arrays and an int for their size.

**Output:** This routine returns a double precision dot product value.

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
E = dot(S, T, Asize);
```

Printing the results

```c_cpp
cout << E;
```

yields:

```c_cpp
8
```

**Implementation/Code:** The following is the code for Dot()

```c_cpp
#include <iostream>

using namespace std;

double dot(double a[], double b[], int Size)
{
  
  //Value to be output
    double sum = 0;

    //for-loop to multiply individual elements of the two vectors, a and b, at index i
    //then add to the running sum
    for (int i = 0; i < Size; i++)
    {
      sum = sum + (a[i] * b[i]);
    }
    
    //return the sum
    return sum;
}
```
**Last Modified:** February/2019

