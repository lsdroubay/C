**Routine Name:**           dmaceps

**Author:** Landon Droubay

**Language:** C++. The code can be compiled using the GNU C compiler (gcc).

For example,

    gcc dmaceps.cpp

will produce an executable **./a.exe** than can be executed. If you want a different name, the following will work a bit
better

    gcc -o dmaceps dmaceps.cpp

**Description/Purpose:** This routine will compute the double precision value for the machine epsilon or the number of digits
in the representation of real numbers in double precision. This is a routine for analyzing the behavior of any computer. This
usually will need to be run one time for each computer.

**Input:** There are no inputs needed in this case.

**Output:** This routine returns a double precision value for the number of decimal digits that can be represented on the
computer being queried.

**Usage/Example:**

A double precision float is assigned and given the value found from the subroutine. The result is output using `<cout>`

      double dmac = dmaceps()
      cout << dmac;

Output from the lines above:

      53   
      2.22045E-16

The first value (53) is the number of binary digits that define the machine epsilon and the second is related to the
decimal version of the same value. The number of decimal digits that can be represented is roughly eight (E-16 on the
end of the second value).

**Implementation/Code:** The following is the code for smaceps()

```c_cpp
#include <iostream>

using namespace std;

double dmaceps()
{
  // initialize values for one and single epsilon
  double one = 1.0;
  double deps = 1.0;

  // create counter
  int ipow = 0;

  // sum one and epsilon to compare with one
  double CompOne = one + deps;

  // find difference in values. Will approach 0 with each iteration.
  double dmac = CompOne - one;

  //temporary value to be saved and returned when difference reaches 0
  double dmacTemp;

  while (dmac != 0)
  {
    // add to counter
    ipow++;

    // save temporary precision
    dmacTemp = dmac;

    //epsilon is halved in each iteration
    deps = deps / 2;

    // re-evaluate CompOne and dmac
    CompOne = one + deps;
    dmac = CompOne - one;
  }

  // print number of iterations
  cout << ipow << endl;

  return dmacTemp;
}
```
**Last Modified:** January/2019
