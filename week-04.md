# WEEk 04 - L.I.D. (Chapters 9, 10, and, 11)

[![Week Three Video](https://img.youtube.com/vi/nN-O4hOE5-0/0.jpg)](https://www.youtube.com/watch?v=nN-O4hOE5-0)

## Liskov Substitution Principle

- LSP is primarily about guiding the use of inheritance. 
- Every "subtype" should be able to be used as its parent type "all the way up the chain"
- In the first image this is done well

![example of LSP as intended](https://user-images.githubusercontent.com/355561/131423517-9435406a-c5d8-4de5-b670-102f23be7ba0.png)

- in the second this is not

![example of the violation of LSP](https://user-images.githubusercontent.com/355561/131423705-69f4b145-498b-4b8e-b8cb-601b12da4399.png)

- the example in the book is long and convoluted 
- suffice it to say a simple violation of subsitutibility can cause a system's architecture to baloon out of control.

## Interface Segregation Principle

Picture of the BAD way:
![Picture of the BAD way](https://user-images.githubusercontent.com/355561/131425144-66adf14f-d892-4c42-a6d7-ffe7e5547698.png)

Better: add more interfaces!!

![Better: add more interfaces!!](https://user-images.githubusercontent.com/355561/131425439-309eed4e-5fa0-49b2-b44f-b53ac58f13ee.png)

- In general it is considered harmful to depend on code taht you don't actually use.
- In development time it can cause unnecessary recompilations and redeployments. 
  - Great example: [windows nano server](https://www.techradar.com/news/software/operating-systems/why-nano-server-is-the-most-vital-change-to-windows-server-since-windows-nt-3-5-1295803)
  - example of "old server" system [just for the image](https://redmondmag.com/articles/2015/02/05/next-windows-server-cloud.aspx)
  - content of this example to be discussed live in the show. Stay tuned for incoming youtube link after tomorrow night.... or in theory it is already there and I never removed this line of text. That souds like me.
- Something that carries baggage that you don't need can cause you troubles that you didn't expect.

## Dependency Inversion Principle

- the most flexible systems are those where source code dependencies only refer to abstractions
- never depend on CONCRETE classes, instead always write an interface layer whan consuming something
- good software designers and work hard to reduce the volatility of interfaces
  - example: instead of calling a database's SAVE method directly if you call it through an interface you can later swap out your database by editing the ONE file that makes calls to the concrete classes.
- Stable software architectures are those that avoid depending on volitile concretions

### DIP Summary rules
- Don't refer to volatile concrete classes
- Don't derive from volatile concrete classes
- Don't override concrete functions
- Never mention the name of anything concrete and volatile

- The key to the DIP is to ensure that all dependencies point in one direction across the boundry line
- note that the orange dotted lines 

![a picture of a non-well defined boudry system](https://user-images.githubusercontent.com/355561/131431424-ebbdb66f-6482-4329-97a5-e1910859c12c.png)

![a picture of a well-defined boudry line](https://user-images.githubusercontent.com/355561/131430536-217b59f3-3db1-4cc7-9d7a-5e738ac50c4b.png)

- LIVE SHOW: discuss why the second version is is better
- Most systems will contain at least one concrete component (often called `main`)

### Conclusion

- DIP shows up again and again.
- This is the most visible organizing principle
- dependencies should cross boundry lines in one direction
- this is referred to as "**the dependency rule**"



