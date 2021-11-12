# Week 13: Chapter 30 & 31 & 32 The Database is a Detail, The Web is a Detail, The Frameworks are a Detail

## The Database is a Detail

- the data model is NOT a detail it is the STRUCTURE of our application that matters
- the specific underlying technology the database ENGINE is a detail
- the difference between SQL and NOSQL isn't really important when compared to whether you get the data
- functional requirements and CAP theorm affect the technology you choose
- the phsyical limitations of a spinning disk has an impact on how database technology evolved
- storage isn't really important from an architectural perspective, consider that most of the time we actually transform the data after we load it

### Conclusion 

- the organizational structure of data IS significant
- the specific technology you choose is not.

## The Web is a Detail

- the GUI is a detail, the web is a GUI
- the web is just an io device

## The Frameworks are a Detail

- frameworks are a massive commitment for a project
- the framework however, does not make a commitment to you
- many frameworks ask you you inherit their code and therefore violate dependency injection
- your product may outgrow the framework
- they often require you to do things in *their way* as you grow sometimes that prevents you from meeting the needs of your product
- a better framework might come along (jquery -> angular -> react)

### the solution

- do your best to keep the framework at arms length
- create a conversion layer between your business rules and your presentation layer (or even your controller/webhost/whatever)
- business objects should be "plain"

### exceptions

- sometiems you DO need to depend on frameworks, as an example the "string library" of your language is pretty much a given
- it's normal to make compromises here.  Make sure the choices you make are deliberate.

### Conclusion 

- keep the framework behind a bourary (the outermost layer)
