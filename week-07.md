
# Week 7 - Ch.15: What is Architecture? Ch.16: Independence

[![Week Seven Video](https://img.youtube.com/vi/FwXW2u0ytEQ/0.jpg)](https://www.youtube.com/watch?v=FwXW2u0ytEQ)

## Chapter 15 What is Architecture?

- asks who a software architect is and what do they do?
- they are programmers 
  - note _reportedly_ at large organizations liek Microsoft and Google, architects typically don't write code I don't know much about this, but will ask around.
- they are expected to guide their team to a maximally productive process and flow
- they must program to be aware of the pains of their team

> The strategy of architecture is to keep as many options open as possible for as long as possible

- good architecture makes a system easy to
  - understand
  - develop
  - maintain
  - deploy
- the ultimate goal is to minimize lifetime cost of the system while maximizing programmer productivity

### Development

- a small team can work on a monolith without any trouble
- a large team has to decompose the app into segments
- in the early days of development interfaces etc.. can feel like impedements
- in later stages they are critical

### Deployment

- the higher the cost of the deployment the less useful a system is
- a cautioun arond microservices they can get overwhelming

### Operation

- operation (hardware / infrastructure) is not as costly as the salaries of the programmers
- therefore increasing hardware spend is often cheaper and easier 
- vs. things that slow development, deployment and, maintenance
- use cases of a system should be obvious

### Maintenance

- this is the day to day work of programmers
- primary costs: spelunking and risk
- **spelunking** is reading through code and devising the best way to update the system
- **risk** is the chance of unintended consequences

### Keeping Options Open

- keeping software soft means leaving options open
- anything that is a "detail" needs to be left open as long as possible
- systems have 2 major elements: policies and details
- policy is where the value of the system lives
- the best systems make details irrelevant to policy
- the longer you wait to determine details, the more information you have to be able to make the decision properly

> A good archiecht maximizes the number of decisions not made

### Device Independence
### Physical Addressing

- story about hard coding device stuff, basically "yay interfaces" (it's a cool story, but we get it)
- story about another hardware thing they solved but with memory locations

### Conclusion

- carefully separate details from policy
- defer decisions about details as long as possible

## Chapter 16: Independence

Architecture must support:

- **Use cases**
  - our first and primary concern. "what does the system need to do?"
  - design must support use cases
  - design should not dictate behavior (really?)
  - use cases should be plainly visible
- **Operation**
  - architecture matters to OPERATION quite a bit
  - design must support USAGE REQUIREMENTS (requests per second, etc.)
- **Development**
  - any organization that designs a system will produce a design whose structure is a copy of that organization's communication structure
  - split components 
- **Maintenance** (no new info)
- **Deployment** the goal is immediate deployment

### Decoupling Layers

- split things like UI and Logic. 

### Decoupling Use Cases

- in some cases decoupling a use case into its own zone makes more sense

### On Duplication

- beware over reliance on the DRY principle (Don't repeat yourself)
- sometimes components that look similar are very different
- this can be "false" or "accidental duplication"
- watch out for cases where this happens

### Decoupling Strategies

- source code 
- deployment
- services

- hard to know the optimal mode
- the mode may change over time
- to decouple too soon is to increase cost but not necessarily reap the benefit
- to defer this decision, separate as far as possible within your codebase without moving to independant deployment
- this allows things to "go together" as long as possible
- while allowing "simple" separation later in the process

### Conclusion 

- decouple according to the things that are likely to change with time
- wait for "the right time" to split things, but always plan for them to be split eventually.
