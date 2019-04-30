I ran the seperate codes, one with sepeate function calls and one with all of the work inline. 
I did it for 3 seperate matrices: one 10x10, a 1000x1000, and 10000x10000. Using `<chrono` to keep
track of the time each took, the results, in microseconds, is printed below. 
```
Size     Func           Inline      (microseconds)
10        5             34
1000      2.22069e+06   2.47753e+06
10000     2.48458e+09   2.65509e+09
```
The difference in speed is between 10 and 15%. This is not noticeable until you start working
with larger matrices, like the 10000x10000 I did last. In the 1000x1000 even, the difference was 
only 0.25 seconds. A quarter of a second isn't noticeable. In the 10000x10000, the inline code took 
2.8 minutes longer. This difference will obviously grow with even larger systems.
