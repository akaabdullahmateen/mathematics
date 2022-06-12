# Exercise3

**Show that, in the process of transferring a tower under the restrictions of the preceding exercise, we will actually encounter every properly stacked arrangement of n disks on three pegs.**

The starting and ending configurations, by definition, are depicting properly stacked arrangement of the n discs on peg A and peg B, respectively. We only have to show that in the optimal solution, the middle peg also has all the discs stacked in proper arrangement at some time.

```
    |          |          |   
    |          |         A|A  
    |          |        BB|BB 
    |      DDDD|DDDD   CCC|CCC
----|----  ----|----  ----|----
```

We must reach this configuration during the optimal solution. We cannot move the largest disc n onto the smaller stack directly, so the smaller stack needs to be moved to either of the middle peg or peg A. But if we move it to the middle peg, we would not be able to move the disc n to peg B. Therefore, this stack needs to be moved to peg A.

```
    |          |          |   
    |         A|A         |   
    |        BB|BB        |   
    |      DDDD|DDDD   CCC|CCC
----|----  ----|----  ----|----
```

Consider the last disc of this stack: disc n-1. When it is time to move it to peg A, the smaller stack must be on either the middle peg or peg A. If it were on peg A, we cannot move it directly to peg A; so this smaller stack must be on the middle peg.

```
    |          |          |   
    |          |          |   
   A|A         |          |   
  BB|BB    DDDD|DDDD   CCC|CCC
----|----  ----|----  ----|----
```

But we are not allowed to move this second largest disc from peg B to peg A directly. Thus, it must move through the middle peg at some time. When it does, the smaller stack needs to be on either of peg A or the middle peg. If it were on the middle peg, we do not need to prove anything else; because this is the correct configuration we were looking for. If however, the smaller stack were on peg A; we at some point, have to move the second largest disc onto peg A. In doing so, the smaller stack must be on the middle peg. Hence proved.

```
    |         A|A         |   
    |        BB|BB        |   
    |       CCC|CCC       |   
    |      DDDD|DDDD      |   
----|----  ----|----  ----|----
```