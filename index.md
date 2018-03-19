H
ungarian algorithm with an example
Problem to solve
Hungarian algorithm is designed to solve the assignment problem: you have cost matrix, which is a n*n square matrix representing the cost for each worker to do the job, you want to minimize the total cost to finish the work.

The Assignment Problem: Suppose we have n resources to which we want to assign to n tasks on a one-to-one basis. Suppose also that we know the cost of assigning a given resource to a given task. We wish to find an optimal assignment–one which minimizes total cost.

So if we don't emphasize the assignment problem, just find the minimum solution, it's pretty simple. Only to find the minimum in every column, then the job is done.

For example, a cost matrix may look like this:

      J1    J2    J3    J4
W1    82    83    69    92
W2    77    37    49    92
W3    11    69    5     86
W4    8     9     98    23
Algorithm implementation
The Hungarian algorithm is implemented in several steps:

1.Subtract row minimum

      J1    J2    J3    J4    
W1    13    14    0    23    (-69)
W2    40    0    12    55    (-37)
W3    6     64    0    81    (-5)
W4    0     1    90    15    (-8)
2.Subtract column minimum

      J1    J2    J3    J4
W1    13    14    0    8
W2    40    0    12    40
W3    6     64    0    66
W4    0     1    90    0
     (-0)   (-0)    (-0)   (-15)
3.Cover all zeros with a minimum number of lines

We will now determine the minimum number of lines (horizontal or vertical) that are required to cover all zeros in the matrix. All zeros can be covered using 3 lines:

      J1    J2    J3    J4    
W1    13    14    0    8    
W2    40    0    12    40      x
W3    6     64    0    66    
W4    0     1    90    0      x
                       x
4.Create additional zeros

First, we find that the smallest uncovered number is 6. We subtract this number from all uncovered elements and add it to all elements that are covered twice. This results in the following matrix:

      J1    J2    J3    J4
W1    7    8      0     2
W2    40   0     18     40
W3    0    58     0     60
W4    0    1     96     0
Now we repeat 4 and test on 3 until minimum number of lines required to cover all zeros in the matrix equals to n.

At this moment shown as below, minimum number of lines required to cover all zeros in the matrix equals to n, this means we have a possible optimal solution (denote in !)

      J1    J2    J3    J4
W1    7    8      0 !    2   x
W2    40   0 !    18     40  x
W3    0 !  58     0      60  x
W4    0    1      96     0!  x
