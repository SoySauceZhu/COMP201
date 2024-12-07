# Lecture 14 Design Methodology
## Software Deign
  - the design process is to derive a software solution that satisfy requirements. 

## What is a good system
  - Useful and usable
  - Reliable (low coupling)
  - Flexible (low coupled, high cohesion)
  - Affordable (Reusability)
  - Available (dev cost optimized by reusing)

## Module Interface
  - abstraction
  - encapsulation: others cannot know the internal info unless interface allows
  - change of internal state of a module doesn't affect other part of the system

## Principles for good design
  - Linguistic Modular Unit
    - i.e. Java classes. BASIC language is not Linguistic
  - Few interfaces
    - Module communicate with as few others as possible. i.e. facade structure
  - Small interfaces
    - The interface should concise, aka Loose coupling. Messaging between modules should be minimum
    - The receiver does not change data of sender. i.e. using immutable data (string, ~~array,ptr,etc~~)
  - Explicit interfaces
    - The interface and document should be clear. i.e. Who is communicating with who
  - Information hiding
    - Make everything private

## Coupling
  - loose coupling means changes in a components not affect other components
  - bad practice is 'shared variables/control event'
  - good practice is 'decentralization / store states inside objects instead of shared repo'
  - OOP is loosely coupled. Because no shared state and communication achieved by message passing. However, each object always coupled with its super-class

## Cohesion
  - each components only handle one problem logically
  - Inheriting attributes from super-class weakens cohesion
  - various levels:
    - coincidental Cohesion
    - logical association
    - temporal Cohesion
    - communication Cohesion
    - sequential Cohesion
    - functional Cohesion
    - object cohesion
  - cohesion & encapsulation:
    - cohesion: how good the functionality of module is organized logically
    - encapsulation: how good the data and methods are protected

## Reusability
  - Reusability ensures low cost of software

## Stepwise Refinement
  - Top-down split problems
  - Recursively refine
  - Until problem can be solved in 7-lines for example

## Good Practice: High Cohesion, Loose Coupling with good interface
  - If so, the module is easy to reuse or even pluggable


