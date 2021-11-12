# WEEK 06 - Component Coupling

[![Week Six Video](https://img.youtube.com/vi/9FfKqlJToGU/0.jpg)](https://www.youtube.com/watch?v=9FfKqlJToGU)

A summary of this week's chapter is pretty simple make sure your code dependencies have no "cycles" which is to say all dependencies should flow in one direction only.

## the Acyclic Dependencies Principle

> allow no cycles in your component dependency graph

- the author introduces two concepts:
  - *morning after syndrome*: cod you were working on earier doesn't work in future because another developer changed a component elsewhere
  - *the weekly build*: in order to ensure MAS doesn't happen you reduce deployment frequency
  - both are listed as problems (with good reason)
  
### eliminating dependency cycles

- the solution is to partition the development environment into reusable components
- patitioned components must be appropriately versioned so OTHER components can decide when to update their dependency
- changes in partitioned components do not need to have an immediate effect on other teams
- to make this work you must monitor, manage and, maintain the dependency structure over time
- there can be no "cycles" or cirrcular dependencies

![Directed Acyclic Graph (DAG)](https://user-images.githubusercontent.com/355561/133002424-901c9ee9-98c3-439f-94d9-111c56fcac4b.png)

### The effect of a cycle in the DAG

![The effect of a cycle in the DAG](https://user-images.githubusercontent.com/355561/133002634-ec9ef62c-8e88-412f-8c47-32faa3365502.png)

- when there are cycles in your dependency graph it can be difficult to figure out what order to build your components in.

### Breaking the Cycle

- one option is to apply the dependency inversion principle

![inverting a dependency with an interface](https://user-images.githubusercontent.com/355561/133002927-c9921ea1-88a2-43d6-b971-89ca402d8442.png)

- another option is to create a new component which both components depend on.

![breaking the cycle with a new component](https://user-images.githubusercontent.com/355561/133003150-59faf94a-6798-4318-97e9-a968a55944dd.png)

### The Jitters

- This dependency flow issue is an ongoing process which requires it be constantly monitored over the lifetime of your project.
- component structure cannot be designed from the top down, insttead it is a system that evolves over time as the system  grows and changes
- component structure cannot be planned effectively in advance
- component flow diagras do nothing to describe the FUNCTIONALITY instead they describe the BUILDABILITY and MAINTAINABLILTY of a project

## the Stable Dependencies Principle

> depend in the direction of stability

- designs cannot be static.
- some components must be volotile
- we should plan for volatility by ensuring the more volatile a component is the less likely we are to depend on it
- many factors make a component hard to change
  - size
  - complexity
  - clarity of code
  - number of other components that depend on it

![the responsible component should be designed to be mroe stable](https://user-images.githubusercontent.com/355561/133003658-c04729fb-36ed-4034-b698-3b75e19638c8.png)

![the dependant component can be designed to be more volitile](https://user-images.githubusercontent.com/355561/133003706-a7dbcd7f-2537-4413-872e-c0b83ffb40b6.png)

- The component in the above diagram may contain only an interface as such it may be referred to as an ABSTRACT compnent.

### Stability metrics

- the author spends a lot of time discussing making stability _measurable_
- he presents multiple formulas based on number of dependencies and dependents
- in theory we should calculate stability and work to reduce that by adopting the techniques above (DIP and Shared dependencies).
- not worth digging into the complexity formulas, consider IDE tools may exist which do these calcualtions for us

## The Stable Abstractions Principle
 
> a component should be as abstract as it is stable

- there is a description of a formula for measuring how abstract a class is
- not particularly useful IMO but for the arguments that follow it is important to believe that you can measure both
  - abstractness
  - stability

## visually mapping the quality of a system's architecture

- this part is interesting BUT a lot of work so is unlikely to happen
- the author describes a concept he calls the main sequence
- we have established that we can measure DEPENDENCY and ABSTRACTNESS
- THUS we can also graph those things.
- AND we can place every class' score on a graph of D vs. A

We get something that looks like this 

![a sample graph blank](https://user-images.githubusercontent.com/355561/133009578-370117ff-f576-4b75-b685-22000ddd7712.png)

- **Useless** a class that nothing depends on and has no concrete code (an orphaned interface)
- a **pain** a class that many things depend on, but is also changing all the time (a database)
- Typically we want classes to live along the main sequence with clusters in the top left and bottom right
- classes can then be further measured in this regard for their distance from the main sequence
- this can help us find areas of concern in our applications

![a made up sample graph measuring a system](https://user-images.githubusercontent.com/355561/133009910-bc4ff233-a718-463d-8288-eb55f662673f.png)

- that final statistic distance from the main sequence can then give us a line graph per component of its COMPLEXITY over time.

