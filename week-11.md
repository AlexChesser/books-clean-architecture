# Week 11: Chapter 24 & 25 & 26 Partial Boudries, Layers and Boundaries, The Main Component

[![Week Eleven Video](https://img.youtube.com/vi/Xm5tL_NvO98/0.jpg)](https://www.youtube.com/watch?v=Xm5tL_NvO98)

## Chapter 24 Partial Boundaries

- architectural bouraries are expensive
- they take a LOT of extra work NOW for a payoff LATER which may not ever happen as requirements change and we learn ne things about the system.
- in many cases the effort to separate can be deemed too high
- three options for dealing with this
  - skip the last step
    - in these cases, consider doing everything you can to make them easy to split, but leave them in the same component.
    - be warned that over time, without attention boudaries in these skip-the-last-step systems will weaken
  - one dimensional boudaries
    - outer rings can depend on inner rings, but don't worry about making two-way separations 
  - facades
    - have a class load all the other classes
    - be warned of the transitive dependency
    - consider a way to STUB other loaded classes when not needed
    
### Conclusion 

- part of the job is deciding what will probably need to be separated one day.
- important to consider this while designing a system

## Chapter 25 Layers and Boundries

### Chapter summary

in the context of an extensive example focused on gaming, the author explains how a 200 line video game file could be re-architected into a wildly complex system by using simple architectureal principles.

Overall it is a good illustration with respect to the ways we might work on things.

The system talks about creating multiple layers for language, or multiple control schemes, data-storage paradigms. It is a good illustration but nothing we haven't seen in previous chapters. No need to dig too deeply here.

### Conclusion

- as archictechts we must carefully recognize when additonal layers are needed
- boundaries when drawn get _expensive_ and as such their adoption should be delayed when possible. 
- they are also expensive to add later in the process.
- over-engineering is often worse than under-engineering
- pay attention to the system as it evolves
- note where boundaries MAY be required
- only add them at the exact perfect time.
- "when the cost of implementing them becomes less than the cost of ignoring them"
- how do you know? you guess *correctly* :)

## Chapter 26 The Main Component

- every system has an entrypoint.
- in many programming frameworks this is called `main` 
- it does not have to be, but for sake of argument we will assume this
- the `main` component is siad to be the ultimate detail. 
- in fact it is typically the one file where all concretions are determined. which impementations of specific interfaces are going to get used? This is typically decided in `main`.
- `main` loads all other plugins
- if you had different versions of an app you could do that by creating different versions of main. (for example a test version vs dev, prod or stage)
- this is subtly different than a config file
- a different main could be deployed for each environment, coutry, jurisdiction, customer, *whatever*

- not much point to this chapter really :)
