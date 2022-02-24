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
#### length
- The length of a string w, denoted by |w|, is the number of symboles in the string.
- We will frequently need to refer to the empty string, which is a string with no symbols at all.
- It will be denoteed by λ.
- The following simple relations
  - |λ| = 0  empty string
  - λw = wλ = w

#### substring
- Any string of consecutive symbols in some w is said to be a substring of w.
- If 
  - w = vu,
  - then the substrings v and u are said to be a prefix and a sufix of w, respecitvely.
    - For example, if w = abbab, then {λ, a, ab, abb, abba, abba, abbab} is the set of all prefixes of w, while bab, ab, b are some of suffixes.

#### the sum of 2 strings concatenation = the sume of 2 strings lengths
- Simple properties of string, such as their length, are very intuitive and probably need little elaboration.
  - For example, if u and v are strings, 
  - then the length of their concatenation is the sum of the individual lengths, that is,
    - |uv| = |u| + |v|
    - But although this relationship is obvious, it is useful to be able to make it precise and prove it.
    - The technuques for doing so are important in more complicated situations.  


#### Example 1.8

- Show that |uv| = |u| + |v| holds for any u and v.
- To prove this, we first need a definition of the length of a string.
- We make such a definition in a recursive fashion by
  - |a| = 1
  - |wa| = |w| + 1 

### 2. Grammar

#### concept of the formal grammars

- A grammar for the English language tells us whether a particular sentence is well-formed or not.
- A typical rule of English grammar is "a sentence can consist of a noun phrase followed by a predicate."
  - 〈sentence〉 -> 〈noun_pharse〉〈predicate〉
- This is not enough to deal with actual sentences.
- We must now provide definitions for the newly introduced constructs (noun_pharse) and (predicate).
  - If we do so by
    -  〈noun_pharse〉 -> 〈article〉〈noun〉,
    -  〈predicate〉->〈verb〉
    -  and if we associate the actual words "a" and "the" with 〈article〉, "boy" and "dog" with 〈noun〉,
    -  and "run" and "walks" with 〈verb〉,
    -  then the grammar tells us that the sentences "a boy runs" and "the dog walks" are properly formed.
    -  If we were to give a complete grammar, then in theory, every proper sentence could be explained this way.
 - This exmple illustrates the definition of a general concept in terms of simple ones.
 - We start with the top-level concept, here 〈sentence〉,
 - and successively reduce it to the irreducuble building blocks of the language.
 - The generalization of these ideas leads us to formal grammars.  

#### Definition 1.1: V T S P
- A grammar G is defined as a quadruple
  - G = (V, T, S, P)
  - 1. V: v is a finite set of objects called variables.
  - 2. T: T is a finite set of objects called terminal symobls.
  - 3. S: S ∈ V is a special symbol called the start variable.
  - 4. P: P is a finite set of productions.  
  - the sets V and T are nonempty and disjoint


#### profuction rule

- The production rules are the heart of a grammar;
- they specify how the grammar transforms one string into another, and through this they define a language associated with the grammar.
- In our discussion we will assume that all production rules are of the form
  - x -> y
  - where x is an element of  (V ∪ T)^+  and y is in (V ∪ T)^*.
  - The productions are applied in the following manner:
    - Given a string w of the form
      - w = uxv,
      - we say the production x -> y is applicable to this string, and we may use it to replace x with y therby obtaining a new string
      - z = uyv
      - This is written as
      - w  




## Chapter 2 Finite Automata

### Finite accepter
- This type of automation is characterized by having no temporary storage.
- Since an input file can not be written, a finite automation is severly limited in its capacity to "remeber" things during the computation.
- A finite amount of informtion can be retained in the control unit by placing the unit into a specifice state.

- But since the number of such states is finite, a finite automation can only deal with situations in which the information to be stored at any time is strictly bounded.

### 2.1 Determinstic Finite Accepter

#### Deterministic Accepters and Transition Graphs
- a deterministic accepter has internal states, rules for transitions from ont state to another, some input, and ways of making decisions.

#### definition of deterministic finite accepter (dfa)
- A deterministic finite accepter or dfa is defined by the quintuple
  - M = (Q,Σ,δ,q0,F)
  - where 
  - Q is a finite set of internal states,
  - Σ is a finite set of symbols called the input alphabet
  - δ : Q × Σ → Q is total function called the transition function
  - q0 ∈ Q is the initial state
  - F ⊆ Q is the a set of final states.
#### dfa operation process
- A deterministic finite accepter (dfa) operates in the following manner:

  - At the initial time, it is assumed to be in the initial state q0, with its input mechanism on the leftmost symbol of the input string.
  - During each move of the automation, the input mechanism advances one position to the right, so each move consumes one input symbol.
  - When the end of the string is reached, the string is accepted if the automation is in one of its final states.
  - Otherwise the string is rejected.
  
  - The input mechanism can move only from left to right and reads exactly one symbol on each step.
  - The transitions from one internal state to another are governed by the transition function δ.
    - for exmaple, if
    - δ(q0, a) = q1
    - then if the dfa is in state q0 and the current input symbol is a, the dfa will go into state q1.   
#### transition graphs   

## Chapter 3 Regular languages and regular grammars

### 3.1 Regular expressions
- a language is regulare if there exists a finite accepter for it.
- therefore, every regular language can be described by some dfa or some nfa.
#### formal definition of regular expression
- We construct regular expressions from primitive constituents by repeatedly applying certain recursive rules.
- This is similar to the way we construct familar arithmetic expressions.
- Let Σ be a given alphabet.
- Then
- 1. Ø,λ and a ∈ Σ are all regular expressions. These are called primitive regular expressions.
- 2. If r1 and r2 are regular expressions, so are r1 + r2, r1.r2, r1* and (r1)
- 3. A string is a regulare expression if and only if it can be derived from the primitive regular expressions by a finite number of applications of the rules in (2).
 
- For Σ = {a,b,c}, the string
 
  - (a+b+c)* .(c+Ø)
  - is a regular expression, since it is constructed by application of the above rules.
    - For examplem if we take r1 = c and r2 = Ø, we find that c + Ø and (c + Ø) are also regular expressions.
    - Repeating this, we eventually generate the whole string.
    - On the other hand, (a + b +) is not a regulare expression, since there is no way it can be constructed from the primitive regular expressions.

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


