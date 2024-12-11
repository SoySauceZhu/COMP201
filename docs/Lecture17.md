
# Lecture 17 

## Object Oriented Programming

## Object Oriented
  - object incorporate both data structure and behavior
  - System functionality is expressed in terms of object services 

## Object
- behavior + state + identity
    - state
        - state of an object is all the data that it encapsulated
        - objects has a number of attributes
        - some attributes are mutable (address, reference) at the immutable
    - behavior
        - an object can understand certain messages, the messages is normally fixed like the set of attribute it has 
  - identity 
    -objects are not defined just by the current value of their attributes
    - the state of an object may change but is still the same object logically 

- Firstly, don't think water and object will have, instead think what will it do for the system
- objects are potentially reusable components
- An object is the thing you can interact with, i.e. You can send your request and get reaction.
- NB: How object behave may change as the current internal state of the object varies
- pros: no centralized data, only communicate by messaging. Independent encapsulated easy for maintenance

## message
  - a message includes a selector, i.e. the method that returns the message. 
  - A message may have arguments 

## interface
  - the public interface of a object defines which messages will be accepted
  - an object can also send message to self, this is managed by public or private interface
  - public interface: any part of the system can use
  - private interface: object itself or other privileged components of the system
  - An object can have several interfaces that from different view of point

## Class
  - each object is an instance of a class
  - class defines the message understandable as well as how object will response
  - each instance has his own state, but share a same `static` state of the class
  - A class encapsulates data and behavior, hiding the Implementation details

## Inheritance
  - inheritance is the sharing of attributes and operations in the hierarchy relationship
  - subclass(superclass)
  - Object class is always coupled to its superclass

## Polymorphism
```java
Doctor dc1 = new Surgeon("Mingjie");
Doctor dc2 = new GeneralPracticer("mingjie");

public void callDoctor(Doctor dc) {
  // You can pass dc1 or dc2 as argument in this function
}
```

## Dynamic Binding
The `print` method is bind dynamically to the subclass in the main method
```java
public class Printer {
  public void print() {
    System.out.println("Printer");
  }
}

public class LaserPrinter extends Printer{
  public void print() {
    System.out.println("LaserPrinter");
  }
}

public static void main(String[] args) {
  Printer p = new LaserPrinter();
  p.print(); // ==> "LaserPrinter"
}
```

## UML
  - UML is a language for specifying, visualizing and documenting

