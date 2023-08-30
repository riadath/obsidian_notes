# <u><mark style="background: #FFF3A3A6;">Finite Automata</mark></u>

## State Diagram

![[Pasted image 20230827045319.png | 500x200]]

 - $q_0, q_1, q_3$ are states . $q_0$ is the start state and $q_2$ is the final state (also called accept states)
- arrows are called transitions 
- For some input string i.e. "1011" the output is either accept or reject

## Formal Definition
![[Pasted image 20230827050159.png | 700x250]]

## Finite Automata for Figure 1.4
![[Pasted image 20230827063930.png | 600x250]]

- If $A$ is the set of all strings that machine $M$ accepts, we say that $A$ is the language of machine $M$ and write $L(M) = A$. We say that $M$ recognizes $A$ or that $M$ accepts A

## Formal Definition of Computation
![[Pasted image 20230827065415.png | 700x200]]

### <mark style="background: #BBFABBA6;">A language is called a <u>Regular Language</u> if some finite automaton recognizes it</mark>

## Regular Operations
![[Pasted image 20230827071354.png | 650x250]]
### Theorem 1.25 
![[Pasted image 20230827071812.png | 600x100]]
### Proof 
![[Pasted image 20230827072259.png | 650x500]]
## Theorem 1.26
![[Pasted image 20230827072542.png | 600x300]]



# <u><mark style="background: #FFF3A3A6;">Nondeterminism</mark></u>

- When the machine is in a given state and reads the next input symbol, we know what the next state will be—it is determined. We call this deterministic computation. In a nondeterministic machine, several choices may exist for the next state at any point.
## NFA Examples

### Ex 1.30
![[Pasted image 20230827082144.png | 600x250]]
##### Equivalent DFA
![[Pasted image 20230827082220.png | 600x300]]

### Ex 1.33
It accepts all strings of the form 0 k where k is a multiple of 2 or 3. accepts $\epsilon$ , 00,000,0000 but not 00000
![[Pasted image 20230827082335.png | 400x300]]

### Ex 1.35
![[Pasted image 20230827082614.png | 200x200]]


## Formal Definition of NFA
![[Pasted image 20230827083921.png | 600x250]]
### Ex 1.38
![[Pasted image 20230827084032.png | 500x300]]
### Computation of NFA : Similar to DFA (above)


## Equivalence of NFA and DFA 
### Proof
![[Pasted image 20230828222940.png | 600x500]]
![[Pasted image 20230828222955.png | 600x400]]

### Corollary 1.40
- A language is regular if and only if some NFA recognizes it.

## Theorem 1.45
- The class of regular languages is closed under the union operation
![[Pasted image 20230830093047.png | 500x350]]

## Theorem 1.47
The class of regular languages is closed under the concatenation operation.
![[Pasted image 20230830093136.png | 500x350]]

## Theorem 1.49
The class of regular languages is closed under the star operation.
![[Pasted image 20230830093243.png | 500x250]]'



