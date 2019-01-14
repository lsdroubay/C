# Math 4610 Fundamentals of Computational Mathematics Software Manual Template File
This is a template file for building an entry in the student software manual project. You should use the formatting below to
define an entry in your software manual.

**Routine Name:**           smaceps

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc smaceps.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o smaceps smaceps.cpp

**Description/Purpose:** This routine will compute the single precision value for the machine epsilon or the number of digits
in the representation of real numbers in single precision. This is a routine for analyzing the behavior of any computer. This
usually will need to be run one time for each computer.

**Input:** There are no inputs needed in this case. Even though there are arguments supplied, the real purpose is to
return values in those variables.

**Output:** This routine returns a single precision value for the number of decimal digits that can be represented on the
computer being queried.

**Usage/Example:**

The routine has two arguments needed to return the values of the precision in terms of the smallest number that can be
represented. Since the code is written in terms of a Fortran subroutine, the values of the machine machine epsilon and
the power of two that gives the machine epsilon. Due to implicit Fortran typing, the first argument is a single precision
value and the second is an integer.

      double smac = smaceps()
      cout << smac;

Output from the lines above:

      24   5.96046448E-08

The first value (24) is the number of binary digits that define the machine epsilon and the second is related to the
decimal version of the same value. The number of decimal digits that can be represented is roughly eight (E-08 on the
end of the second value).

**Implementation/Code:** The following is the code for smaceps()

```
#include <iostream>

using namespace std;

float smaceps();

int main()
{
  // initialize a variable for the precision
  float smac;

  // call machine presicion function
  smac = smaceps();

  // print results
  cout << "SMac = " << smac << endl;
  return 0;
}

// machine presicion function
float smaceps()
{ 
  // initialize values for one and single epsilon
  float one = 1.0;
  float seps = 1.0;

  // create counter
  int ipow = 0;

  // sum one and epsilon to compare with one
  float CompOne = one + seps;
  
  // find difference in values. Will approach 0 with each iteration.
  float smac = CompOne - one;
  
  //temporary value to be saved and returned when difference reaches 0
  float smacTemp;

  while (smac != 0)
  {
    // add to counter
    ipow++;
    
    // save temporary precision
    smacTemp = smac;
    
    //epsilon is halved in each iteration
    seps = seps / 2;
   
    // re-evaluate CompOne and smac
    CompOne = one + seps;
    smac = CompOne - one;
  }
  
  // print number of iterations
  cout << ipow << endl;

  return smacTemp;
}
```
**Last Modified:** January/2019
