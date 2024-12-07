# Lecture 15 Distributed System Architectures

## Software Architectures
  - Architectural Design: 
    - The early stage of design process, generate description of architecture
    - Focuses on sub-systems (System components) and their communication & control
    - In parallel with other specification design
  
## Architectural Design process
  - System structuring: decompose systems into components and identify the communication
  - Control modelling: determine the model of control relationship between components
  - Modular decomposition: decompose sub-systems into modules

## Sub-systems and Modules
  - Sub-system: operation independently, separately. i.e. JAVA packages, login system
  - Modules: in a sub-system, but work together.  

## Benefit of subsystem modelling
  - Re-assemble subsystem to build new system

## Architectural Models
  - Different models may be produce during the design process
  - Different perspective gives different Architectures
    - Static structural: merely show the components
    - Dynamic process: who is calling how
    - Interface model: define sub-system Interface
    - relationship model: data-flow model

## System structuring
  - decompose the system into interacting components (sub-systems)
  - use Block Diagram

## Repository Models: data exchange between subsystem
  - central database: suitable for large data
  - internal database: each components pass data to each other

## Client-Server Architecture
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

## Control model
  - centralized control
    - one of subsystems control others
    - call-return model
      - top-down subroutines, using in sequential system
      - NB, in a sequential model, events are also handled parallel in background in higher level
    - manager model
      - concurrent system, control subsystems in parallel
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

## Modular decomposition
  - object model
    - loosely coupled objects and well-define interfaces
    - include: classes, attribute, operations
  - data-flow model
    - defines the batch sequential pipeline, used in data processing system
    - not suitable for interactive system

