# Computer-language-theory

## Proof Techniques
1. proof by induction:
  - 1. base
  - 2. assumption(inductive assumption)
  - 3. proof 
2. proof by contradiction

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
3. difference (−): S1 − S2 = {x: x ∈ S1 and x ∉ S2}
4. complementation: 
   - The complement of a set S, denoted by consists of all elements not in S. 
   - To make this meaningful, we need to know what the universal set U of all possible elements is. 
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

- We see from this example that we can prove that a set is countable if we can produce a method by which its elements can be written **in some sequence.** 
- We call such a method an **enumeration procedure.** 
- Since an enumeration procedure is some kind of mechanical process, we can use a Turing machine model to define it formally.
- Not every set is countable. 
- As we will see in the next chapter, there are some uncountable sets.
- 
#### enumeration procedure exists(not algorithm) -> countable
- But any set for which an enumeration procedure exists is countable because the enumeration gives the required sequence.
- Strictly speaking, **an enumeration procedure cannot be called an algorithm since it will not terminate when S is infinite.** 
- Nevertheless, it can be considered a meaningful process, because it produces well-defined and predictable results.

## 1.2  languages, grammars, automata
- Three fundamental ideas are the major themes of this book:
- 1. languages
- 2. grammars
- 3. automata
- In the course of our study we will explore many results about these concepts and about their relationship to each other.
- First, we must understan the meaning of the terms.

### 1. Languages
- We start with a finite, noneempty set ∑ of symbols, called the alphat.
- From the individual symbols we construct strings, which are finite sequences of symbols from the alphabet.
  - For example, if the alphabet  ∑ = {a, b}, then abab and aaabbba are strings on ∑.
  - With few exceptions, we will use lowercase letters a, b, c,...for elements of ∑ and u, v, w,...for string names.
  - We will write, for example,
    - w = abaaa
    - to indicate that the string named w has the specific value abaaa.

#### concatenation
- The concatenation of two stings w and v is the string obtained by appending the symbols of v to the right end of w, that is, if
  - w = a1a2...an
  - and
  - v = b1b2...bm
  - then the concatenation of w and c, denoted by wv, is
  - wv = a1a2...anb1b2...bm
#### reverse
- The reverse of a string is obtained by writing the symbols in reverse oeder; if w is a string as shown above, then its reverse w^R is
  - w^R = an ... a2a1
### length
- The length of a string w, denoted by |w|, is the number of symboles in the string.
- We will frequently need to refer to the empty string, which is a string with no symbols at all.
- It will be denoteed by λ.
- The following simple relations
  - |λ| = 0  empty string
  - λw = wλ = w

### substring
- Any string of consecutive symbols in some w is said to be a substring of w.
- If 
  - w = vu,
  - then the substrings v and u are said to be a prefix and a sufix of w, respecitvely.
    - For example, if w = abbab, then {λ, a, ab, abb, abba, abba, abbab} is the set of all prefixes of w, while bab, ab, b are some of suffixes.

### the sum of 2 strings concatenation = the sume of 2 strings lengths
- Simple properties of string, such as their length, are very intuitive and probably need little elaboration.
  - For example, if u and v are strings, 
  - then the length of their concatenation is the sum of the individual lengths, that is,
    - |uv| = |u| + |v|
    - But although this relationship is obvious, it is useful to be able to make it precise and prove it.
    - The technuques for doing so are important in more complicated situations.  


## Chapter 2 Finite Automata
- 

### 5.2 Parsing and Ambiguity
- We have so far concentrated on the generative aspects of grammars.
- Given a grammar G, we studied the set of strings that can be derived using G.

- In cases of practical applications, we are also concerned with the analytical side of the grammar:
  - Given a string w of terminals, we want to know whether or not w is in L(G).
  - If so, we may want to find a derivation of w.
  - An algorithm that can tell us whether w is in L(G) is a membership algorithm.
  - The term parsing describes finding a sequence of profuctions by which a w ∈ L(G) is derived.  

### 5.3 Context-Free grammars and programming languages
- One of the most important uses of the theory of formal languages is in the definition of programming languages and
- in the construction of interpreters and compilers for them.
- The basic problem here is to define a programming language precisely and to use this definition as the starting point for the writing of efficient and reliable translation programs.
- Both regular and context-free language are important in achieving this.
-  regular language & context-free language:
     - regular languages are used in the recognition of certain simple patterns that occur in programmong languages,
     - but as we need context-free languages to model more complicated aspects. 


### BNF (Backnus-Naur form)
- As with most other languates, we can define a programming language by a grammar.
- It is traditional in writing on programming languages to use a convention for specifying grammars called the Backus-Naur form or BNF.
-  This form is essence the same as the notation we have used here, but the appearance is different.
-  In BNF, variables are enclosed in triangular brackets.
-  Terminal symbols are written without any special marking.
-  BNF also uses subsidiary symbols such as | , much in the way we have done.

## Chapter 7 Pushdown Automata

- The description of context-freee languages by means of context-free grammars is convenient, 
- as illustrated by the use of BNF in programming language definition.


