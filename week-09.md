# Week 9: Chapter 19 & 20 & 21 Policy and Level, Business Rules, Screaming Architecture

[![Week Nine Video](https://img.youtube.com/vi/UJZXWqwQKAI/0.jpg)](https://www.youtube.com/watch?v=UJZXWqwQKAI)


## Policy and Level  

- software systems are statements of policy
- policy can be broken down into many smaller statements of policy
  - how business rules are calculated
  - reports are formatted
  - input data validated
- the art of architecture  separating policies from
  - each other
  - grouping them in the ways they change
  - forming components into a _directed acyclic graph_
  - Every component in your project should be part of a DAG

### Level

- level is the distance from the inputs and outputs
- I/O is the lowest level

![a sample encryption program](https://user-images.githubusercontent.com/355561/135954466-bfd358d5-f1ce-4549-9811-6efef983d757.png)

![improved encryption program](https://user-images.githubusercontent.com/355561/135954993-46dda187-0c5a-4f17-8d20-d322b0a884d0.png)

![a simplified diagram](https://user-images.githubusercontent.com/355561/135955183-b1f33cf6-6414-447b-8253-5405888d9ee9.png)

- the reason for these designs is the fact that higher level policies change less frequently.
- you're less likely to alter the algorithm to encrypt something than you are to change the way that data enters your encrypter
- the higher level component will change for more critical reasons
- the lower level ones will change
  - more frequently
  - with more urgency
  - for less important reasons
- lower level components shodl be plugins for higher level components

Chapter 20: Business Rules

- BR are rules and procedures that make or save the business money (profit)
- these rules would generate profit EVEN if executeed manually
- these are considered _Critical Business Rules_
- CBR usually require DATA
- We call this data _Critical Business Data_
- Critical business RUles and Critical Data are inextricably bound

### Entities

- an entity is the name for a class we use in order to combine both rules and data in one place

![a sample entity](https://user-images.githubusercontent.com/355561/135956035-55af7dee-e955-4618-b423-e6e04213c99c.png)

### Use cases

- not all business rules are entities
- some rules are aroud automation, for example they create profit only by being automated
- use cases do not define the method of delivery, merely what happens.
- user stories which define logical flow
- use cases are application specific
- use cases therefore depend on entities (data) entities do not depend on use cases

### Request and response models

- use cases take data objects in and return data objects out
- they do NOT return HTML/SQL/formatted anything save for things like JSON or other serialized data
- this ensures a lack of dependencies

### Conclusion

- business rules are the reason that software systems exist
- they should therefore remain *pure* and have as little dependencies as possible
- they should also be as independent as possible
- (and write tests!)
 
## Chapter 21: Screaming Architecture

notes from edx:

- A quick glance at a component should tell you what the component does, not what framework you used.
- Don't have a big collection of apps all together, co-locate them by feature. (i.e. have a "learning" folder filled with the apps related to learning)

### Theme of an architecture

- architecture exists to support the use cases
- good architecture makes the use cases obvious
- the first concern is to be usable
- in a good architecture it should not matter whether you deliver on web, console, desktop, api
- prevent the framework from taking over

### testable architectures

- you should be able to test all use cases without a framework in place
- you shouldn't need
  - a web server
  - a database
- entities should be "plain old objects"
- entity inputs should be pure-data, as should outputs
  - formatting and presenation should be secondary and added after
- testing should be able to be done in-situ without any frameworks in place

### Conclusion

- your architecture should tell the reader what the system does, not what framework you used
- a reader of your code should be able to know what the use cases are and potentially not even know how the system is delivered
