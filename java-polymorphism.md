# POLYMORPHISM

## Intro

- a method can do different things and have many different forms of results depends on the object that it is acting on. (These objects share the same superclass.)
- Enables you to “program in the general ” rather than “program in the specific
- Polymorphism means that a variable of a supertype can refer to a subtype object. Example: Bird is a subtype of AnimalObject and AnimalObject is a supertype for Bird
- Key concept of polymorphism Relying on each object to
  know how to “do the right thing” in response to the same
  method call is.
- Make the class design flexible and extensible with customized implementation.
  - i.e. new classes can be added with little modification, as long as the new classes are part of the inheritance hierarchy;
  - The only parts of a program that must be altered to
    accommodate new classes are those that require direct
    knowledge of the new classes that we add to the
    hierarchy.
- Method overriding allows a subclass to use all the general definitions from the superclass and add specialized definitions. i.e. enable code resue.
- Polymorphism is work with both interface and inheritance.
  - Interfaces are particularly useful for assigning
    common functionality to possibly unrelated classes
  - This allows objects of these classes to be
    processed polymorphically objects of classes
    that implement the same interface can respond
    to all of the interface method calls
