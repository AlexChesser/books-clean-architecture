# Week 10: Chapter 22 & 23 The Clean Architecture, Presenters and Humble Objects

[![Week Ten Video](https://img.youtube.com/vi/AW9lCWFaX_U/0.jpg)](https://www.youtube.com/watch?v=AW9lCWFaX_U)

## 22 The Clean Architecture

- Interestingly the book takes a moment to name a few other "types" of architecture while noting their similarities
  - Hexagonal architecture - aka ports and adapters [book](https://www.oreilly.com/library/view/growing-object-oriented-software/9780321574442/)
  - DCI - <https://en.wikipedia.org/wiki/Data,_context_and_interaction>, <https://dzone.com/articles/dci-architecture-is-visionary>
  - BCE - <https://www.ivarjacobson.com/publications/books/object-oriented-software-engineering-1992>
- each architecture has the following common themes (each theme has been discussed in an earlier chapter)
  - independent of frameworks
  - testable
  - independent of the UI
  - independent fo the database
  - independent of any external agency - specifically business rules
  
### the diagram

![The clean architecture](https://user-images.githubusercontent.com/355561/137592260-4e16479e-a281-4a33-a1f0-147aa9900463.png)

### the dependency rule
  
> source code dependencies must point only inward towards higher level policies

- nothing on an inner ring can know anything about an outer one.
- **entities** - encapsulate enterprise-wide business rules
- **use cases** - captures application specific business rules
- **interface adapters** - convert data for passing across the layers
- **frameworks and drivers** - glue code that communicates between layers (inward)

### crossing boudaries

- use the dependency inversion principle 
- no "name" on an outer ring should be mentioned by an inner ring
- when we pass data inward it shold always be in the form that is most convenient for the inner circle (reducing external dependency)

### Conclusion

- by spearating the architecture into layers using DIP we greate a system that is instrinsically TESTABLE
- when external parts become obsolete we can replace them with a minimum of fuss. (think "new javascript framework" day)

## Chapter 23 - Presenters and Humble Objects

### the humble object pattern

- separate behaviors that are hard to test from behaviors that are easy to test
- it is difficult to write tests that need to be able to see the screen
- with the _Humble Object Pattern_ we can separate classes into presenter and view
- external humble object references:
  - <https://martinfowler.com/bliki/HumbleObject.html>

  >  By making untestable objects humble, we reduce the chances that they harbor evil bugs.
  
  - https://stackoverflow.com/questions/5324049/what-is-the-humble-object-pattern-and-when-is-it-useful
- a view is hard to test as such we keep all code out of these objects when possible and pass in ONLY pre-calcualted data
- the calcualtions can be done elsewhere and as such, can be tested
- the term VIEW MODEL could be uysed to make an onject that only returns strings to a view.
- with no logic or calculation happening WITHIN the view itself, the calcualtions become testable.

### Database Gateways
 - gateways contain the methods for create, read, update, delete (crud)
 - we do not allow SQL in the use case layer
 - gateways can be replaced with stubs in a unit testing situation
 - gateways allow you to write tests without having an actual database

** ^^^ this is super important and cool**

### Conclusion

- architectural boudaries can be used to effecitvely increase the testablity of the system.

