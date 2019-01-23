**Routine Name:**           AbsErr

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc AbsErr.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o AbsErr AbsErr.cpp

**Description/Purpose:** Computes and returns the absolute error in the approximation of 
a number x by another number y.

**Input:** A double precision value and another that represents an approximation of that value.

**Output:** This routine returns the absolute error between two numbers.

**Usage/Example:**

Two double-precision numbers are initialized

```c_cpp
double real = 5.667;
double approx = 5.5;
```
Call routine to find absolute error.

```c_cpp
double error = AbsErr(approx, real);
```

Printing the results yields

```c_cpp
0.167
```

**Implementation/Code:** The following is the code for AbsErr()

```c_cpp
#include <iostream>

using namespace std;

double AbsErr(double x, double y)
{
  // initialize value for error
  double err;
  
  /*
  absolute error is the absolute value of the
  difference of the values 
  */
  err = abs(y - x);

  //return value
  return err;
}
```
**Last Modified:** January/2019
