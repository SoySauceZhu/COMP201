
# Lecture 15 Distributed System Architectures

- Software Architectures
  - Architectural Design: 
    - The early stage of design process, generate description of architecture
    - Focuses on sub-systems (System components) and their communication & control
    - In parallel with other specification design
  
- Architectural Design process
  - System structuring: decompose systems into components and identify the communication
  - Control modelling: determine the model of control relationship between components
  - Modular decomposition: decompose sub-systems into modules

- Sub-systems and Modules
  - Sub-system: operation independently, separately. i.e. JAVA packages, login system
  - Modules: in a sub-system, but work together.  

- Benefit of subsystem modelling
  - Re-assemble subsystem to build new system

- Architectural Models
  - Different models may be produce during the design process
  - Different perspective gives different Architectures
    - Static structural: merely show the components
    - Dynamic process: who is calling how
    - Interface model: define sub-system Interface
    - relationship model: data-flow model

- System structuring
  - decompose the system into interacting components
  - use Block Diagram

- Repository Models: data exchange between subsystem
  - central database: suitable for large data
  - internal database: each components pass data to each other

- Client-Server Architecture
  - components
    - servers
    - clients: call on services
    - networks
  - Feature
    - distribution of data
    - effective use of networks
    - easy to extend new servers or upgrade
    - No shared data, data interchange inefficient
    - Redundant management in servers
    - Hard to parse server and services

- Control model
  - centralized control
    - one of subsystems control others
    - call-return model
      - top-down subroutines, using in sequential system
      - NB, in a sequential model, events are also handled in background in higher level
    - manager model
      - concurrent system, control subsystem in parallel
      - real-time system control
  - event-based control: server's handler listening for events then response accordingly 
    - broadcast model
      - integrating different subsystem to response and working together
      - control message is not embedded in event
      - system not know when event happens
      - NB, most of time is idle
      - i.e broadcast -> {LED1, LED2, LED3, LED4}
    - interrupt-driven model
      - NB, most of time is busy
      - used in real time system, fast response
      - there is a handler in each interrupt types. i.e. INTERRUPT A -> LED1, INTERRUPT B -> LED2 

- Modular decomposition
  - object model
    - loosely coupled objects and well-define interfaces
    - include: classes, attribute, operations
  - data-flow model
    - defines the batch pipeline



# Lecture 14 Design Methodology
- Software Deign
  - the design process is to derive a software solution that satisfy requirements. 

- What is a good system
  - Useful and usable
  - Reliable (low coupling)
  - Flexible (low coupled, high cohesion)
  - Affordable (Reusability)
  - Available (dev cost optimized by reusing)

- Module Interface
  - abstraction
  - encapsulation: others cannot know the internal info unless interface allows
  - change of internal state of a module doesn't affect other part of the system

- Principles for good design
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

- Coupling
  - loose coupling means changes in a components not affect other components
  - bad practice is 'shared variables/control event'
  - good practice is 'decentralization / store states inside objects instead of shared repo'
  - OOP is loosely coupled. Because no shared state and communication achieved by message passing. However, each object always coupled with its super-class

- Cohesion
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

- Reusability
  - Reusability ensures low cost of software

- Stepwise Refinement
  - Top-down split problems
  - Recursively refine
  - Until problem can be solved in 7-lines for example

- Good Practice: High Cohesion, Loose Coupling with good interface
  - If so, the module is easy to reuse or even pluggable


