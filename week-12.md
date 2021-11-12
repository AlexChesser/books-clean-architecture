# Week 12: Chapter 27 & 28 & 29 Services: Great and Small, The Test Boundary, Clean Embedded Architecture


## Services: Great and Small

- services may seem to be strongly decoupled from each other
- services appear to support independence of development and deployment 
- these are both only partially true

- some services are no more than expensive function calls
- as such they are not necessarily architecturally significant

### Service Benefits: the fallacies

- **decoupling fallacy**: services can often be coupled according to the data they share
- **fallacy of independent development and deployment**: services that are coupled via shared data can't be developed and deployed without cross team coordination
- clients and services can be so tightly coupled as to have no architectureal significance whatsoever

## The Test Boundary

- tests are part of the system
- they participate in the archtecture
- they often dictate the architecture
- tests by their nature MUST follow the depenency rule
- they always depend inward
- tests are ALWAYS the outermost circle 
- tests represent the model that all other systems should follow

### Design For Testability

- _The Fragile Tests Problem_: tests that are so britle and that they break often create what are called **Fragile Tests**
- **Fragile Tests** therefore can make a system more rigid because developers will be reluctant to make changes that are likely to break tests
- One solution to this problem is _Don't depend on volitile things_
- design the system and the tests such that business rules can be tested independent of the GUI (or other systems)

### The testing API

- create a specific API that the tests can use to verify the business rules
- allow tests to bypass security, expensive resources, and force the system into particular testable states

### Structural coupling

- if each class has its own tests, this can create fragile tests
- instead a testing api can be used to HIDE that complexity
- **security concerns**: a testing api that bypasses all other concerns can be dangerous.
- best to leave your tests and API into a standalong component that does not deploy with the wider app 

## Clean Embedded Architecture

> Although software does not wear out, firmware and hardware become obsolete, thereby requiring modifications

### what is firmware?

- firmware is software that:
  - is written to non volitile memory like a ROM, EPROM or FLASH MEMORY
  - set of instructions programmed on a hardware device
  - software embedded in a piece of hardware
  - software on read-only-memory

(consider as and example, your BIOS is firmware)

### general advice

**The three activities for writing software**
1. make it work
2. make it right
3. make it fast

- plan to throw the first one away
- learn what works and then find a better solution

The rest of the chapter summarizes Clean Architecture principles in the event you're writing for an embedded device.
Key points being 

- software and firmware intermingling is an anti pattern. Keep them separate
- **HARDARE** is a detail do your best to encapsualte away from it.
- create a hardware abstraction layer  - which is to say encapsulate your firmware away from the software running on that firmware
- **Operating System** is a detail, abstract it from the firmware and abstract the software from the OS
- other than that, it's pretty much just regular architecture
