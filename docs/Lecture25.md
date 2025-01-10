# Software Testing

## Cyclomatic Complexity
- The number of tests to test all control statement is the cyclomatic complexity
- Cyclomatic complexity = number of edge (any edges) - number of node (any node no matter the type) + 2
- NB: program flow diagram is directed
- Dynamic program analyzer can show which path (lines in code) aren't executed

## Independent Path
Independent path is the path that introduce new nodes into test

## Integration testing
- Integration testing is mostly black box, it's not practical to execute every path in a enormous system.
- It's hard to locating where the error is. You just need to locate which module the error is in.
- Incremental integration testing reduces this problem

## Incremental Integration Testing
Regression testing: future tests also test previous test cases again
Test harness: automatically create test data and record the results

## Integration testing approach
- Top-down testing: test general function first
    - Top-down is good at: Architectural validation, System demonstration, Easy to create tests
- bottom-up testing: test sub-system integration first
    - System that suitable for bottom-up: OOP, real-time system (find which part slows down the whole system), strict performance required system(we can measure the performance of individual parts)

## Interface testing
- To detect faults due to interface errors or invalid assumption about interfaces
- Used when the module will be integrated to make larger systems.
- Very useful in OOP
- Good practice: 
    - Design test that the parameters of invoked procedure are at extreme end of range 
    - Always test pointer with null pointer
    - Stress testing in message passing system: send a lot of messages at same time
    - In shared memory system, vary the order that components are activated


## Interface types
- Parameter interfaces
- Shared memory interfaces: memory addr is shared between procedures
- Procedural interfaces
- Message passing interface

## Interface errors
- Interface misuse: make error in using the interface i.e. wrong arguments
- Interface misunderstanding: the caller object holds incorrect assumption about the behavior of the called component
- Timing error: The processing speed of different components is different, so out-of-date information will be accessed

## Stress testing
- System should fail gracefully when receives too many messages, but not catastrophically
- System should stop receiving or tell others to stop sending messages before it cannot hold any more
- Exercise the system beyond its maximum design load
- Distributed system should aware of it more seriously

## Object-Oriented Testing
- All methods and functions should have tested to work correctly
- There is no obvious 'top' to the system for top-down integration and testing

## Testing levels
- Testing operations related to objects
- Test object classes
- Test cluster of cooperating object
- Test the complete OO system
  
## Object Class Testing
A Complete test coverage of a class involves: 
- All associated operations with the objet
- Setter and getter 
- Exercising the object in all possible states

Inheritance makes it more difficult to design object class test since the information may not stored locally

## Object integration
You can test your OO program by integrate them up.
Clustering testing is for testing a cluster of cooperating objects

## Cluster testing approach
- Use-case or scenario testing
- Thread testing: Test the system response as threads through the system. (thread basically means a series of operation)
- Object interaction testing: Test sequence of object interactions taht stop when an object operation does not call on services from another object
