# Part II: Programming Paradigms 

[![Week Two Video](https://img.youtube.com/vi/QkC7Z34SQTI/0.jpg)](https://www.youtube.com/watch?v=QkC7Z34SQTI)

Pages 19 to 67 (48 pages)

## Chapter 03 - Paradigm Overview

- **Structured Programming**: prevents the programmer from using a GOTO statement
- **Object-Oriented Programming**: prevents the programmer from "indirect control" (calling private functions, accessing private variables)
- **Functional Programming**: Prevents the programmer from assigning variables (without strict controls)

**Summary** - in each instance a programming paradigm is centered around REMOVING the ability to do something.

### Conclusion 

The three main concers with architecture
- Function
- Separation of components
- Data management

Discussion points: 
- GOLANG and RUST are also languages which impose strict controls on the programmer which prevents the user from inadvertently creating memory leaks
- TypeScript prevents a user from doing all sorts of stuff, making javascript "safer" to work with

## Chapter 04 - Structured Programming

### Proof

- Dijkstra decided to apply mathematical proofs to algorithms. 
- discovered you can't prove something in code with GOTO statements
- created `if/then/else` and `do/while` control structures

- GOTO Statement Considered Harmful 
- **Functional Decomposition** by breaking down code into smaller functions we can mathematically PROVE that it works.
- Formal proofs are possible, but way too much work.
- Testing shows the presence, not the absence, of bugs
- We show that code is correct by *failing to prove it is incorrect* despite our best efforts

### Functional Decomposition:

Architectural best pactice #1 - break large amounts of code into smaller chunks until it is small enough to PROVE.

- This is why we say smaller functions, fewer lines of code per file.

## Chapter 05 - Object-Oriented Programming

- Invented in 1966 when programmers moved a functions to long-term RAM
- They could store "local variables" within the function and they'd stick around.
- Discussion: Consider `this` in Javascript. 
  - Objects are effecively just instances of `functions`

- **Encapsulation** prevents accessing a function's internal variables.
- Inheritence - (not paticularly compelling or relevant)
- Polymorphism 
- OO languages allowed the PLUGIN Architecture to be invented

### Dependency Injection Metaphor

(not foud in clean architecture)

- imagine you're going to a restaurant and you know you want to order a hamburger.
- you go to a food court and stop at each restaruant along the way.
- the restaraunt hands you their INTERFACE: `IMenu`
- you tell them you would like a menu that implements the `IHaveHamburgerMenu` interface
- In the case of Dependency Injection, any restaruant that implements the right menu could be used interchangably

- If you have a FUNCTION that knows it is going to have to call another FUNCTION, you can do that one of two ways:
  - call it directly
  - call it as a parameter
  - When you call it as a parameter, it is dependency injection.

- Why care? By passing functions as parameters we can better separate the code
- If we separate the code far enough, we can deploy it independently (even on separate teams)
- **Independent Deployablility**: when the source code in a component changes, only that component needs to be redeplopyed
- **Independent Developability**: If the modules in your system can be deployed independently, they can be developed independently by different teams.
- OO is the ablitity to gain control over dependencies 

## Chapter 06 - Functional Programming

### Immutablity and Architecture

> Why would an architect be concerned with Immutablity? Because all race conditions, deadlocks and, concurrent update problems are due to variables changing.

- consider the REACT framework
- consider ANGULAR 
- _IS_ REACT a functional programming design?
- **Segregation of Mutablity**: if we separate all places where we CHANGE variables from the places where we READ variables, then we cut the location where bugs are complex.

> Well-structured applications will be segregated into those componenets that do not mutate variables and those that do.

- Git as an example of Immutablity - initial commit starts the "variable gets set" each transaction is a "changeset" we read the current value by starting with the initial value and applying each changeset until the most recent entry.


## Conclusion

- The initial foundations of architecture (programming paradigms) are all based on REMOVING a programmer's ablity to do something. Imposing discipline.
- the rules are the same today as there were in 1946.
