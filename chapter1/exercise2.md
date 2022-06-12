# Exercise 2

**Find the shortest sequence of moves that transfers a tower of n disks from the left peg A to the right peg B, if direct moves between A and B are disallowed. (Each move must be to or from the middle peg. As usual, a larger disk must never appear above a smaller one.)**

## Trivial solutions

- T<sub>0</sub> = 0
- T<sub>1</sub> = 2
- T<sub>2</sub> = 8

## Boundary value

- T<sub>0</sub> = 0

## Recurrence

```
   A|A         |          |   
  BB|BB        |          |  
----|----  ----|----  ----|----

    |          |          |    
  BB|BB        |         A|A   
----|----  ----|----  ----|----

    |          |          |    
    |        BB|BB       A|A   
----|----  ----|----  ----|----

    |          |          |    
   A|A       BB|BB        |    
----|----  ----|----  ----|----

    |          |          |    
   A|A         |        BB|BB  
----|----  ----|----  ----|----

    |          |         A|A   
    |          |        BB|BB  
----|----  ----|----  ----|----
```

- We know how to transfer the smaller stack on top of the largest disc from peg A to peg B; this takes T<sub>n-1</sub> moves
- Now the largest disc is moved to the middle peg
- The smaller discs stack from peg B is moved back to peg A, taking anther T<sub>n-1</sub> moves
- The largest disc is moved to peg B
- The smaller stack is moved back to peg B, on top of the largest disc; this takes yet another T<sub>n-1</sub> moves

Therefore, the moves, T<sub>n</sub> required for moving all the n discs from peg A to peg B under the given rules must be less than or equal to the moves required for the given procedure; that is:

T<sub>n</sub> <= 3T<sub>n-1</sub> + 2	(2.1)

- Initially, when all discs are stacked on peg A, we must move the top n-1 discs (ultimately) to the middle peg or peg B. If we end up moving all these n-1 discs to the middle peg, then the largest disc (disc n) needs to be moved directly to peg B - which is forbidden. Therefore, we must move the top n-1 discs to peg B. We already have found the most optimal solution to do that; it takes T<sub>n-1</sub> moves
- Now the largest disc must be moved to the middle peg
- This largest disc cannot be moved on top of the smaller discs on peg B; therefore, this stack must be moved back to peg A - taking another T<sub>n-1</sub> moves
- The largest disc is moved to peg B
- The smaller disc stack must be moved back to peg B, taking another T<sub>n-1</sub> moves

This is the least amount of moves possible, therefore:

T<sub>n</sub> >= 3T<sub>n-1</sub> + 2	(2.2)

These two inequalities, together with the trivial solution yields:

T<sub>0</sub> = 0
T<sub>n</sub> = 3T<sub>n-1</sub> + 2	(2.3)

## Closed form

|    **n**    |  0  |  1  |  2  |  3  |  4  |  5  |
|:-----------:|:---:|:---:|:---:|:---:|:---:|:---:|
| **T<sub>n** |  0  |  2  |  8  | 26  | 80  | 242 |

T<sub>n</sub> = 3<sup>n</sup> - 1

## Proof by induction

T<sub>n</sub> = 3T<sub>n-1</sub> + 2
T<sub>n</sub> = 3(3<sup>n-1</sup> - 1) + 2
T<sub>n</sub> = 3<sup>n</sup> - 1
