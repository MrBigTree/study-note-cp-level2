# Java OOP

## POLYMORPHISM

### Intro

- a method can do different things and have many different forms of results depends on the object that it is acting on. (These objects share the same superclass.)
- Enables you to “program in the general ” rather than “program in the specific
- Polymorphism means that a variable of a supertype can refer to a subtype object. Example: Bird is a subtype of AnimalObject and AnimalObject is a supertype for Bird
- Key concept of polymorphism Relying on each object to know how to “do the right thing” in response to the same method call is.

### Powerful Technique

- Make the class design flexible and extensible with customized implementation.

  - i.e. new classes can be added with little modification, as long as the new classes are part of the inheritance hierarchy;
  - The only parts of a program that must be altered to accommodate new classes are those that require direct knowledge of the new classes that we add to the hierarchy.

- Method overriding allows a subclass to use all the general definitions from the superclass and add specialized definitions. i.e. enable code REUSE.
- Polymorphism is work with BOTH interface and inheritance.
  - Interfaces are particularly useful for assigning COMMON functionality to possibly UNRELATED classes
  - This allows objects of these classes to be processed polymorphically objects of classes that implement the same interface can respond to all of the interface method calls

### Tips to remember

- Polymorphism enables you to deal in generalities and let the execution time environments handle the specifics
- objects to behave in manners appropriate to those objects, without knowing their specific types as long as they belong to the same inheritance hierarchy.
- Polymorphism promotes extensibility
  - Software that invokes polymorphic behavior is independent of the object type to which the messages are sent.
  - Therefore, new object types that can respond to the existing method calls can be added into a system without changing the base system.
  - Only the client code that instantiates new objects must be changed to accommodate new types.
- A polymorphic reference is a variable that can refer to different types of objects at different points in time
- The method invoked through a polymorphic reference can change from one invocation to the next
- All object references in Java are potentially polymorphic

### Polymorphism Through Inheritance
- It is the type of the object being referenced, not the reference type, that determines which method is invoked. 
  - Mammal pet = new Mammmal() => pet refers to a Mammal object, it invokes the Mammal version of move
  - Mammal pet = new horse()=> pet refers to a Horse object, it invokes the Horse version of move

### Reference and Inheritance
An object reference can refer to an object of its class, or to an object of any class related to it by inheritance.
For example, Holiday class is the parent of Christmas , then a Holiday reference could be used
to point to a Christmas object. Holiday special = new Christmas(); Clock obj = new AlarmClock();

### Types of Polymorphism
- static (compile-time Polymorphism) method overloading
- dynamic (run-time Polymorphism) method overriding
  - call an overridden method is resolved at runtime.

### Method Overriding in Java
- child class choose to have its own implementation to existing methods in parent class
- The method in the parent class is said to be “overridden”
- The method in the child class is said to be “overriding”
- advantage:
  - child class choose to have a different implementation
  - child class choose to use parent class method
  - parent class code not need to be changed
- Rules for method overriding
  - Argument list of overriding method must match the overriden method
  - Access modifier of the overriding method cannot be more restrictive than the overriden method of parent class
  - private, static, and final method cannot be overriden as they are local to the class. 
  - static method can be re-declared in the subclass 

### dynamic binding / late binding
- Binding is the association of method call to the method body.
- binding occurred at run time, then that line of code would call different method with same method name depends on the object.
