# Week 05 - Chapters 12, 13 and Additional Resources

[![Week Five Video](https://img.youtube.com/vi/4WVClmGNRK0/0.jpg)](https://www.youtube.com/watch?v=4WVClmGNRK0)

## The additional resources (meh)

1. http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod
1. https://groups.google.com/g/comp.object/c/WICPDcXAMG8?hl=en&pli=1#adee7e5bd99ab111

## Chapter 12 - Components

- this chapter is mainly a history lesson on the reasons why components exist it gives good perspective on the why and how this design emerged and makes sense
- Components are the units of deployment in a system 
- The smallest entities that can be individually deployed
  - DLLs, jar files, gem files, an NPM MODULE are all _components_
- Components are independently DEPLOYABLE
- Components are independently DEVELOPABLE

### A Brief History of Components

- Programmers used to control the memeory location of their code. 
- Programs would quite literally specify the exact memory address their function would live at (wild)
- If a programmer wanted to work with an existing "LIBRARY" they would have to write their code such that it did not conflict with the memory locations of the library they were consuming

In the following image we see a sample of what this might have been like. Every block of code started with a number for its memory start lcoation, but so did function libraries. 

![memory layout example](https://user-images.githubusercontent.com/355561/132256424-24e63a73-147a-429b-b3f5-d434e30acb31.png)

So in order to use them effectively you might have to split your application across multiple memory locations according to the package you wanted to use.

![image](https://user-images.githubusercontent.com/355561/132256551-065ec8df-f1fb-48bd-aaff-5809e1c75dbd.png)

- at some point these became dynamically relocatable and their locations were determined by the OS automatically
- as computers got fast enough to load functions from DLLs at runtime "components" were born  
- Dynamically linked files that are plugged together at runtime are our components 
  - Swapping a "component" at runtime could change a program's function without requiring a full redeploy

## Chapter 13 - Component Cohesion

- Component cohesion is about determining which classes get placed in which packages
- there are three guiding principles that we will discuss today
  - **REP**: Reuse/Release Equivalence Principle
  - **CCP**: Common Closure Principle
  - **CRP**: Common Reuse Principle

### Reuse/Release Equivalence Principle

> _the granule of reuse is the granule of release_

- Reusing code was one of the oldest promises of Object Oriented Programming
- Independently released MODULES must have versions such that programmers know what is in them
  - live discussion: what if DLLs didn't have version numbers?
    - What happens when you try and use an arrow function in IE6?
    - <https://caniuse.com> the ultimate example of why we need version numbers?
- There shold be some overarching _THEME_ to any code that is released as a component
- Classes or modules that are logically GROUPED together shold be RELEASED together
- The author calls this "weak advice" because there is nothing we can empirically say other than it should "make sense"
- The author ALSO says that "we'll know it when we see it" when something doesn't make sense

### Common Closure Principle

> _Gather into components those classes that change for the same reason and at the same time. Separate those classes that change at different times and for different reasons._

- for most applications maintainablility is more important than reusablity
- if changes are confined to a single component then we only have to redeploy one compoenent
- if two classes are so tightly bound that they always change together, then they belong in the same component.
- this is the **SRP** for components (single responsibility)

### Common Reuse Principle

> _Don't force users of a component to depend on things they don't need_

- don't put a class in a component unless it is inseparable from that component.

### the mutually exclusive nature of these principles

- the three principles are at odds with each other

![replication of the "tension diagram"](https://user-images.githubusercontent.com/355561/132257143-fd9d6d91-a9f1-4911-a38f-ab8f77c24596.png)

- the ART of computer architecture comes into play here, it is inevitable that you will have to violate at least one principle at any given time ... you've got to dynamically choose which rule to break
- A good architect finds a position against the tradeoffs that meets the _current_ needs of the team
- Those needs **will** change over time
  - live discussion: startup vs. scale up
