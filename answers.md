# CMPS 6610 Problem Set 03
## Answers

**Name:** Keith J. Mitchell


Place all written answers from `problemset-03.md` here for easier grading.




**1b.**

The iterate function processes each element exactly one time making the total work equal to: $W(n) = O(n)$. The span is sequentially dependent as each element is processed only after the previous element is, making the span equal to: $S(n) = O(n)$.

**1d.**

The work is $W(n) = O(n)$ as the recurrence would be $W(n) = 2W(n/2) + 1$. This recurrence is leaf dominated and would lead to each element being processes exactly one time as well. The span would then be $S(n) = O(logn)$ as the reccurence is $S(n) = S(n/2) + 1$ which is balanced with k being equal to log base 2 of n.

**1e.**

The work for this algorithm would be $W(n) = W(n/3) + W(2n/3) + 1$ which equals a work of $W(n) = O(n)$. The span would be $S(n) = S(2n/3) + 1$ which gets a span of $O(logn)$.

**2a.**

Algorithm: Iterate through $\mathcal{A}$ while keeping a set `seen` to track elements already included. Append each new element to the output list.  

SPARC specification:  
```
dedup(A: list) -> list
Pre: A is a finite list of n elements.
Post: Returns a list containing each unique element of A, preserving
      their first occurrence order.
```

The work for this algorithm would be: $W(n) = O(n)$. The span would be: $S(n) = O(log n)$

**2b.**

Algorithm: Concatenate all lists, distribute elements across processors by hashing, remove duplicates locally, then merge results into a global set.

SPARC specification:  
```
multi-dedup(A: list of lists) -> set
Pre: A = [A0, A1, ..., Am] where each A of i is a list of n elements.
Post: Returns a set of distinct elements appearing in any list (Ai).
```

The work for this algorithm would be: $W(mn) = O(mn)$. The span would be: $S(mn) = O(mn)$

Comparison: This has more total work than part (a), since we must process all $mn$ elements, and the span is higher because of distributed merging.

**2c.**

Yes. Sequence operations are useful:  

- **iterate** for getting a count of the total number of times a specific item appears in a list  
- **map** for hashing elements to processors  
- **filter** to remove/ignore items that are duplicates and returning distinct lists 
- **reduce** for merging sets across processors

These operations help organize and parallelize the deduplication process efficiently. 

**3b.**

Iterative parenthesis matching with `iterate`:  
- Recurrence: $W(n) = W(n-1) + 1$, $S(n) = S(n-1) + 1$  
- **Work:** $W(n) = O(n)$  
- **Span:** $S(n) = O(n)$ 


**3d.**

Parenthesis matching with `scan`:  
- Mapping step: $O(n)$ work, $O(1)$ span.  
- Scan step: $O(n)$ work, $O(\log n)$ span.  
- Reduce step: $O(n)$ work, $O(\log n)$ span.  
- **Total Work:** $O(n)$  
- **Total Span:** $O(\log n)$


**3f.**

Divide-and-conquer parenthesis matching:  
- Recurrence: $W(n) = 2W(n/2) + 1$, $S(n) = S(n/2) + 1$  
- **Work:** $W(n) = O(n)$
- **Span:** $S(n) = O(\log n)$ 