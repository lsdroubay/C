## Task 10

[This article](https://www.researchgate.net/publication/316511026_Parallel_Algorithms_for_Matrix_Multiplication) details a process for doing matrix-matix multiplication, C = A*B. The matrix is first split into four blocks of similar size. 
Then C is calculated by doing 7 matrix multiplications and 18 add/subtracts. This is applied recursively until the block dimensions reach a
threshold value.

1   C12 = A21 - A11
2   C21 = B11 + B12 
3   C22 = C12 * C21
4   C12 = A12 - A22
5   C21 = B21 + B22
6   C11 = C12 * C21 
7   C12 = A11 + A22 
8   C21 = B11 + B22 
9   T1 = C12 * C21 
10  C11 = T1 + C11 
11  C22 = T1 + C22 
12  T2 = A21 + A22 
13  C21 = T2 * B11 
14  C22 = C22 - C21 
15  T1 = B21 - B11 
16  T2 = A22 * T1 
17  C21 = C21 + T2 
18  C11 = C11 + T2 
19  T1 = B12 - B22 
20  C12 = A11 * T1 
21  C22 = C22 + C12 
22  T2 = A11 + A12 
23  T1 = T2 * B22 
24  C12 = C12 + T1 
25  C11 = C11 - T1

