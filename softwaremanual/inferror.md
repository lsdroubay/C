**Routine Name:**           Infinity Norm Error

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc inf_error.cpp

will produce an executable **./a.exe** than can be executed. 

**Description/Purpose:** Computes and returns the error of two vectors of equal size using the infinity norm.

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
E = inferror(S, T, Asize);
```

Printing the results yields

```c_cpp
9
```

**Implementation/Code:** The following is the code for inferror()

```c_cpp
#include <iostream>

using namespace std;

double inferror(double a[], double b[], int Size)
{
  //temp variable to replace b with error array
  double temp;

  //initialize to zero to ensure iterations can start
  double max = 0;

  //initialize a double to be temporary placeholder for each iteration
  double maxtemp;

  //for-loop to take abs error of corresponding elements of the two vectors, a and b, at index i
  //replace b vector with error values
  for (int i = 0; i < Size; i++)
  {
    temp = abs(a[i] - b[i]);
    b[i] = temp;
    maxtemp = abs(b[i]);

    //if the value is greater than the current max, set as new max
    if (maxtemp > max)
    {
      max = temp;
    }
  }

  //return the sum (Infinity Norm)
  return max;

}
```
**Last Modified:** February/2019

