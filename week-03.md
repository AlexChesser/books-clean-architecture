# Week 3 - Design Principles  S.O.L.I.D

[![Week Three Video](https://img.youtube.com/vi/GPt0tETT1rk/0.jpg)](https://www.youtube.com/watch?v=GPt0tETT1rk)

### A WARNING

- The chapters on SOLID principles do not dwell on explaining what SOLID principles ARE. If you have not yet learned them or want a refresher, take a moment to go through some content on them before proceeding (or cross your fingers :) that's OK too)
- The chapters ahead will focus on the SOLID principles implications for architecture
- some "refresher content"
  - a "children's book" on SOLID : https://medium.com/backticks-tildes/the-s-o-l-i-d-principles-in-pictures-b34ce2f1e898 
  - Wikipedia https://en.wikipedia.org/wiki/SOLID
  - <https://www.youtube.com/watch?v=zHiWqnTWsn4> from the author himself (80 minutes)
  - my personal favorite explanations are from Jason Weimann @ Unity3d.college they're very specific to writing games in Unity, but they're designed in a way which really makes the content "concrete" in a real way with a fun visual example. Plus, he has good production value. Don't forget if you watch on 2x speed you can get through it a lot quicker.
    -  S: <https://www.youtube.com/watch?v=Eyr7_l5NMds> (11 min)
    -  O: <https://www.youtube.com/watch?v=wYkzeKghjsI> (8 min) 
    -  L: <https://www.youtube.com/watch?v=eXPBR3WlRGY> (8 min)
    -  I: <https://www.youtube.com/watch?v=ll6bxQGkyCk> (10 min)
    -  D: <https://www.youtube.com/watch?v=fGshe3ILKnA> (15 min)

## Section III - Design Principles  

- The goal of SOLID principles are the creation of "mid-level" software structures that:
  - tolerate change
  - are easy to understand
  - are the basis of components that make can be used in many software systems (reusable?)
- mid-level code is defined as sitting at the "module" level. Which is to say more than a function, (potentially) less than a complete system.

- **SRP**: the single responsiblity principle - each software module has one and only one reason to change.
- **OCP**: the open-closed principle - code should be able to be changed by ADDING new code as opposed to changing existing code
- **LSP**: the Liskov substitution principle (attributed to Barbara **Liskov**) - parts must adhere to a CONTRACT that allows those parts to be SUBSTITUTED for one another.
- **ISP**: the interface segregation principle - avoid depending on anything that doesn't get used.
- **DIP**: the dependency inversion principle - code should not depend on DETAILS.

- In case you missed the warning above :) 
> the chapters in CL focus on the architectural implications of SOLID and not what SOLID *is*

**Further note**: these chapters get pretty dense from a technical perspective. It's a good choice to go slow instead of doing all 5 in one week :)

## Chapter 07 - SRP - Single Responsiblity

- Any given source code file should be responsible to one and only one actor.
- failure to do so may result in two symptoms
  - ACCIDENTAL DUPLICATION
  - MERGE ISSUES
- Consider the example of an employee payroll system 

### BAD example: an employee payroll system
- There exists an Employee class with 3 functions
  - calculatePay()
  - reportHours()
  - save()
- each of these three functions is primarily consumed by a different department
  - _calculatePay_ is used by the finance department.
  - _reportHours_ is used by managers 
  - _save_ is used by Human Resources
- by putting all three functions in the same source-code-file
  - there is a chance of multiple teams competing to get critical changes to their business logic executed.
  - there is a chance that the business logic is used by different teams and _potentially_ one team's changes could impact another's
    - for if `reportHours` was used by managers AND finance, and managers wanted a report on hours on-site, while finance wanted a special calculation for OVERTIME hours then the data reported could become wrong for one of the two parties if changes are made without coordination.

### Solutions to "the bad way"
- move each function into a different file and importantly, ensure each file does not depend or even require knowledge of the others
  - **discussion**: this could result in a violation of the DRY principle (don't repeat yourself) should we consider ranking rules of code? Does SRP outrank DRY?
  - **storytime**: I've actually really badly violated SRP in favor of DRY and it caused problems on numerous occasions. This prompt is to remind me to tell the story of a real world project that I worked on where I violated SRP in favor of DRY and the result some significant problems. The live story will be told in the youtube associated with this week's work.
- **Solution number two**: use what is known as a _FACADE pattern_ to address the additional complexity added in soution # 1 above.
  - refreshers: <https://www.coursera.org/lecture/design-patterns/2-1-5-facade-pattern-prQp9> (6 min), no speed option but otherwise high quality video
  - article: <https://refactoring.guru/design-patterns/facade>
  - wiki: <https://en.wikipedia.org/wiki/Facade_pattern>
  - <https://www.youtube.com/watch?v=K4FkHVO5iac> (16 min) Christopher Okhravi. this one feels clearest to me.

## Conclusion

- the SRP is about functions and classes, but it is critical and returns to us twice more in different forms
- SRP has an analog at the next level up from code (component level) called "Common Closure Principle"
- at the system design (architectural) level it is the principle that defines the concept of **Architectural Boundries** (which we learn about later, it's fine that we don't understand what this means now)

## Chapter 08 - OCP - Open Closed Principle

- a software artifact should be open for extension and closed for modification
- organize dependencies and systems in a ONE WAY fashion. 
  - discussion: We will _hopefully_ learn how to do this later in the book, for now it is sufficent to know what we should do

if a system in a MODULE (A) should be protected from changes in another MODULE (B), then make sure that (B) depends on (A)

in this first image we see a system where each MODULE depends in one direction only 

![a sample open / closed system](../closed-ciagram.png)

Simple right?!

### warning warning warning - the next image is deliberately complex and might make you cry! (I did)

however when we look at the internals there is significant complexity that is locked away

![a sample open / closed system](../Untitled%20Diagram.png)

- notice however how changes to changes to any systems outside of interactor (the business rules) will have no impact on any other system.
- notice also that the additional complexity and work around that nightmare image above (the interfaces mainly) are all in place in order to ensure all dependencies are pointed in the correct direction.
- the extra work on the nightmare image above is all about serving the business' need in order to maintain long-term project velocity
- by ensuring dependencies flow in one direction a new system (eg mobile screen view) could be added without disrupting any of the other systems.

## Conclusion 

- the goal of the OCP is to make the system easy to extend without incurring a high impact in terms of the cost of change
- by partitioning the system into components 
- by arranging the components in a dependency hierarchy
- higher level components are protected from changes in lower level components.
