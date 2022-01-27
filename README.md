# Computer-language-theory

## Sets
- A set is a collection of elements, without any structure other than membership. 
- To indicate that x is an element of the set S, we write x ∈ S. 
- The statement that x is not in S is written x ∉ S. 
- A set can be specified by enclosing some description of its elements in curly braces; for example, the set of
integers 0, 1, 2 is shown as 
  - S ={0, 1, 2}

### The usual set operations
1. union (∪): S1 ∪ S2 = {x: x ∈ S1 or x ∈ S2}
2. intersection (∩): S1 ∩ S2 = {x: x ∈ S1 and x ∈ S2} 
3. and difference (−): S1 − S2 = {x: x ∈ S1 and x ∉ S2}
4. complementation: 
   - The complement of a set S, denoted by consists of all elements not in S. To make this meaningful, we need to know what the universal set U of all possible elements is. 
   - If U is specified, then
     - S' = {x: x ∈ U, x ∉ S} 



## A Universal Turing Machine
### infinite set: countable and uncountable sets
- Some sets are finite, but most of the interesting sets (and languages) are infinite.




### countable sets

- For infinite sets,
  - we distinguish between sets that are countable and sets that are uncountable. 
  - A set is said to be countable if its elements can be put into a one-to-one correspondence with the positive integers. 
  - By this we mean that the elements of the set can be written in some order, say, x1, x2, x3,…, 
  - so that every element of the set has some finite index. 
    - For example, the set of all even integers can be written in the order 0, 2, 4,…. 
    - Since any positive integer 2n occurs in position n +1, the set is countable. 
    - there are more complicated examples, some of which may seem counterintuitive. 
 
 ### enumeration procedure
 
 - Take the set of all quotients of the form p/q, where p and q are positive integers.
 - How should we order this set to show that it is countable? 
 - We cannot use the sequence because then would never appear. 
   - 1/1, 1/2, 1/3, 1/4, ...
 - This does not imply that the set is uncountable; in this case, there is a clever way of ordering the set to show that it is in fact countable. 
 - Look at the scheme depicted inFigure 10.17, and write down the element in the order encountered following the arrows. 
 - This gives us
   - 1/1, 1/2, 2/1, 2/2, ...

- Here the element occurs in the seventh place, and every element has some position in the sequence.
- The set is therefore countable.

- We see from this example that we can prove that a set is countable if we can produce a method by which its elements can be written in some sequence. 
- We call such a method an enumeration procedure. 
- Since an enumeration procedure is some kind of mechanical process, we can use a Turing machine model to define it formally.
- Not every set is countable. 
- As we will see in the next chapter, there are some uncountable sets.

- But any set for which an enumeration procedure exists is countable because the enumeration gives the required sequence.
- Strictly speaking, an enumeration procedure cannot be called an algorithm since it will not terminate when S is infinite. 
- Nevertheless, it can be considered a meaningful process, because it produces well-defined and predictable results.

