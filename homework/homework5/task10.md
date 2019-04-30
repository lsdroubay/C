##Task 10

It is mentioned on [this site](https://math.stackexchange.com/questions/2462931/what-are-the-benefits-of-iterative-method-against-lu-decomposition) that direct methods will produce an exact answer for dense, non-singular matrices when roundoff
error doesn't exist. Of course, when working with computers and computational approximations, roundoff error is ever present.
Direct methods will still produce great results when roundoff is small. Reducing/preventing large roundoff error is always a goal.
It is not always avoidable. The same site, which actually quotes our textbook, mentions that direct methods run into issues when 
solving sparse matrices. This produces "fill-in" where methods such as Gauss elimination now puts in values where there was initially
a zero. This increases computational cost and loses the advantage of having a sparse matrix.
Direct methods also cannot benefit from an initial guess iterative methods can. The direct methods have to do the whole thing evry time. 
