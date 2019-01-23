**Routine Name:**           RelErr

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc RelErr.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o RelErr RelErr.cpp

**Description/Purpose:** Computes and returns the relative error in the approximation of 
a number x by another number y.

**Input:** A double precision value and another that represents an approximation of that value.

**Output:** This routine returns the relative error between two numbers.

**Usage/Example:**

Two double-precision numbers are initialized

```c_cpp
double real = 5.667;
double approx = 5.5;
```
Call routine to find relative error.

```c_cpp
double error = RelErr(approx, real);
```

Printing the results yields

```c_cpp
0.0303636
```

**Implementation/Code:** The following is the code for RelErr()

```c_cpp
#include <iostream>

using namespace std;

double RelErr(double x, double y)
{
  // initialize value for error
  double err;

  /*
  relative error is the absolute value of the
  difference of the values divided by the
  absolute value of the approximate value, x.
  */
  err = abs(y - x) / abs(x);

  //return value
  return err;
}
```
**Last Modified:** January/2019
