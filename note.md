# 12: Communication

## Client Server model
- Request-reply

## Layer protocol
- Structure
    - Physical layer
    - Data link
    - Network
    - Transport
    - ~~Session~~
    - ~~Presentation~~
    - Application

- Physical:
    - Mechanical, Electrical, Optical
    - Modulate, synchronize

- Data Link Layer
    - Error detection
    - Frame, check digit
    - Transmit unit: frame
    - Node to node connection, no routing, suitable for local area network (LAN)

- Network Layer
    - Routing: choose the path with minimum delay, not shortest path
    - Implement connection between arbitrary nodes of network
    - Ex. IP protocol
        - Packets are routed independently, maybe different path

- Transport Layer
    - Flow control
    - Packet splitting
    - ordering
    - resending
    - Interface between developer and the underlying network
    - Ex. TCP: transmission control protocol. UDP

- Middleware layer:
    - replace session and presentation layers

- Application
    - application specific protocols
    - Ex. HTTP, FTP, 

## Connection/Connectless transport layer
- TCP: connection-oriented
    - Operations:
        - Open/Close conn
        - Write/Read from conn
    - Reliable but slow
    - Ex. HTTP, IMAP, POP

- UDP: connectionless transmission protocol
    - Sending and receiving datagrams
    - Fixed length messages
    - Fast and unreliable
    - Ex. DNS, VoIP

- Transport layer is the lowest level in developing
    - You can use socket (either SOCK_STREAM for TCP or SOCK_DGRAM for UDP), bud would care lower level

## Socket and Port
- Reliable p2p communication provided by TCP
- Socket is bound to a port (logical concept)

## Identify port:
- Static port (endpoint)
- Dynamical assigned
    - Daemon service (registry center), target service runs forever
- Super-server
    - Response the target port
    - Create and starts the requested service/thread on demand

## Socket in Java
- Socket class
- Write/Read method
- etc

# 13,14: Application Communication Protocol

## Implement HTTP use socket

## Socket:
- Procedure
    - Create ServerSocket constructor
    - Create socket object
    - Create input and output stream
    - Write to/Read from stream
    - Close socket

- Advantage:
    - Customized (app specific protocols)
    - fast, efficient
- Con:
    - Cost effort to change functions
    - hard to maintain
    - Bad at OOP paradigm
    - ...

## Pass an Object
- Serialization
## Middleware
- Middleware provide some general services like:
    - Naming protocol: to access shared resources
    - Security protocol
    - Scaling mechanism, supporting replication and caching

## Middleware communication: RPC, RMI

- RPC: remote process call
    - program is called and executed on remote machine
    - using stub
        - Client stub: the interface to remote functions
        - Server stub: call the actual function on remote machine
        - Client Code->Client Stub->Communication modules(OS)->Server Stub->Service Code
    - Message based: packing/unpacking parameters as well as results
    - Works good if machines are homogeneous
    - IDL: Interface Definition Language. Help RPC to work effectively
    - Summary
        - It is mature, the de-facto standard for communication and application distribution.
        - Well understood
        - Works in many scenarios

- RMI: remote method invocation
    - Components
        - The stub in RMI is a proxy object of remote object
        - The remote stub is a skeleton of object
        - Proxy and Skeleton have a same interface 
        - Distributed object is stored and executed on server
    - Parameter&Result passing
        - Reference: objects that implement `Remote` as remote object. Which will always store and execute on server
        - Value: primitive type and objects that implements `Serializable`. Whose real value and data will be sent on client
    - Code MIgration
        - Better performance: move computation intensive task to lightly loaded machine
        - Disadvantage: Security
# 15: Message Communication

## Different types
- Client(sender) block?:
    - Synchronous
    - Asynchronous
- Server alive at the time?
    - Transient
    - Persistent
- Receipt-based: 'ACK'
- Delivery-based: 'Accept'
- Response-based: ''

## Message Queue
- Support persistent, asynchronous
- Only Guarantee msgs will routed into receiver's MQ eventually
- methods:
    - put
    - get: remove the first. Blocking if empty
    - poll: remove the first. Non-blocking if empty
    - Notify
- Route Architecture:
    - Queue manager can route a msg from source to dest queue
- Applications:
    - Database integration
    - Email
    - Office Automation

## Queue Manager
- A middleware for distributed communication
- Can connect to MQ or another manager
- Form a complete - application level - Overlay Network

## Broker
- A server to transform/interpret different messages formats
- Consisted of a database for conversion rules

# 15.2: Stream Oriented Communication
- Audio and video are time-dependent data streams (continues media)
- Transmission mode:
    - Asynchronous transmission mode
        - No constraints on delivery time
    - Synchronous transmission mode
        - As fast as possible: maximum delay
    - Isochronous mode:
        - Both minimum and maximum end-to-end delay (bounded jittering)
        - Ex. stream
- Stream:
    - Types
        - Simple stream: only one data stream
        - Complex stream:
            - Need synchronization
    - Quality of Service: Most current OS doesn't have native mechanism
        - Timeliness
        - Volume
        - REliability
    - Improve QoS:
        - Buffer: introduce a artificial delay at initial
        - Best effort service: shuffle the packets
            - Neither guarantee delivery, not guarantee in order

- Summary
    - RPC, RMI: synchronized and transient
    - MOM: convenient asynchronous and persistent
    - Stream: useful when dealing with temporally-related data


# 16 Communication Architecture

## Client-Server
- Server
    - Type
        - Iterative/ sequential
        - Concurrent/ Parallel
    - State
        - Stateful
        - Stateless
- Application Layers
    - Three layers
        - User Interface
        - Processing Level
        - Data Level
    - Two tired architecture
        - Split the three layers into two parts
        - Thin client, fat client
    - Multi-tiered architecture
        - Micro-service
        - Proxy Server
        - Vertical: operating different components
        - Horizontal: logically equivalent parts (replication, server farms)

## Other Architectures
- Web applets
    - Requiring applet code from web server and run locally
- P2P
    - Decentralized

# 17 Naming

## Naming service

## DNS Domain Name System

# 18 Clock Synchronization

## Cristian alg
- N.B. Estimated latency

## Berkeley alg
- Find the global average time (including coordinator itself)
- Distribute adjustment amount

## NTP network time protocol

## Logical clocks
- Physical clock will never be correct due to network
- Lamport's logical clock
    - Message are timestamped
- Application:
    - Totally-Ordered Multicast
        - Msgs are sent to MQ and sorted by logical time, and receiver multicast ACK
        - Only MQ with all processors response ACK will be executed

    - Vector Timestamp: Causality



# 19: Fault Tolerance

## Overview
- Fault tolerance is generally achieved through use of redundancy and reliable multi-casting protocols
- also you need to recover from arrow in a DS

## Error in DSs
- Partial failure instead of singleton total failure
- The goal is to mask partial failure


## Failure
- Failure: functional term, caused by error
- Error: Ex. damaged packet, lost packet, caused by fault
- Fault: lowest level. Ex. transmission medium broken
- Fault tolerant system should provide the function even with faults.

## Type of faults
- Transient
- Intermittent
- Permanent

## Type of failure
- Crash
- Omission: server fails to respond request
- Timing failure
- Response incorrect
- Byzantine, Arbitrary failure

## Solution: Redundancy
- Information redundancy
    - extra bits, hamming code, parity bit
- Time redundancy
    - Send and resend and again
- Physical redundancy
    - Replication for software or hardware
    - Ex. Triple modular redundancy: Vote


## Topics: improve fault tolerance in system level
- Process Resilience
    - replicate identical processes as group
    - Flat group
        - Every processes decide on consensus
    - Hierarchical group
        - One coordinator assign one of the process to response

- Reliable Client Server comm
    - dealing with crash masking and omission
    - i.e. in TCP, 'ACK' is used to ensure no omission

- Reliable Group communication
    - Make everyone get the same message, especially when member coming in or quit
    - Multi-casting is unreliable
    - Atomic multi-casting
        - all or none of nodes get the message

- Distributed COMMIT:
    - Every DB conduct consistent operation
    - protocols
        - single-phase commit
        - two-phase commit
            - If coordinator doesn't hear every response, it conduct abortion
            - If participant doesn't hear coordinator's instruction, it can ask for neighbor. The worst case is no one hear from coordinator
        - three-phase commit

- Recovery
    - Backward recovery: checkpoint
        - Maintain checkpoints are costy
        - Same error may happen again
        - Practical impossible: Bank transfer cannot roll back
    - Forward recovery: bring the system to a correct state
        - You need to be aware of any possible error
    - EX.
        - Re-transmission a lost packet is BACKward recover
        - Use hamming code to recover packet is FORWARD recover
    - Checkpoint + Logging
        - Sender based log: record before sending
        - Receiver based log: record before executing
    - Independent checkpoint on two items:
        - Cascading rollback is caused by inconsistent cut
  


# 20: Consensus

## Consensus with Link Failures: NOT POSSIBLE

- Setting: 
    - n processors
    - Any connected undirected network
    - Each processor know the entire network
    - Synchronous Communication
    - Messages may be lost
- Correctness:
    - Everyone makes the same decision
    - If everyone starts at 0, then 0 is the decision; If it's 1, 1 is the decision. Otherwise, go to default value.
    - All processor eventually decide (terminate)

## Consensus with Processor Failure: IS SOLVABLE

- Setting:
    - Processor can crash at any time
    - In a COMPLETE network
    - At most f processors can crash

- Correctness:
    - No processor decide on different value
    - If everyone starts with s, then s is the decision
    - Termination: all non-fault processors eventually decide

- Solution: FloodSet
    - Idea: everyone broadcast until a 'on failure round'
    - Each processor maintains a variable W, containing all items they've heard
    - 'f + 1' round is guaranteed to be fault free, decide at when

- Complexity: n-#processor, b-#bits, f-#round
    - time: f+1 round
    - size of msg: O(nb), (maximum). theta(n), minimum.
    - \# of msg: O( (f+1)n^2 ). (N node sending N msgs each round)

- Correctness proof


# 21: Transaction

## Why synchronize
- Data can be lost duplicated or corrupted if two thread write without sync

## Synchronize types:
- Synchronize clock
    - Actual time: Cristian, Berkeley, NTP
    - Logical time: Lamport Timestamp
- Synchronize concurrent actions

## Transaction
- Function:
    - protect shared the resources: mutual exclusion
    - allow Atomic operation: either success or abort

- Operations:
    - BEGIN
    - END(COMMIT)
    - ABORT
    - READ
    - WRITE 

- Good Properties:
    - ACID

- Types of Txn
    - Flat txn
    - Nested txn
        - Parent txn spawns child txn.
        - problem is when children is commit but parent is aborted
        - Ex. Tavel booking = Airline booking + Hotel booking, Operation on different DB 
    - Distributed txn
        - Ex. Two separated disk act as the same database

- Serializable
  
- Conflict

## Transaction Control Model
- Organization:
    - Txn manager: begin/commit txns (on user's side)
    - Scheduler: Lock/Release, timestamp (Distributed)
    - Data Manager: read/write (Distributed)

## Undo Txn
- Private workspace
    - Copy everything when start a txn
    - Sometimes use index. Instead of copy the whole datapage to private space
- Write ahead log
    - Rollback when abort



# 22: Concurrent

## Terms
- Critical section
- Mutual Exclusion
- Semaphore: the datatype to control mutual exclusion
- Processors cycle:
    - Entry: controlled by mutual exclusion algorithm
    - Critical
    - Exit: controlled by mutual exclusion algorithm
    - Remainder

## Good properties in Mutual excl alg
- Safety: no different access at same time
- Liveness: eventually succeed
    - no deadlock
    - no starvation or lockout

## Deadlock detection
- Timeout
- Explicit lock graph

## COordinate mechanism
- Central
    - easy, fare
    - single point failure, performance
- Distribute
    - Token ring:
        - easy, fare
        - Possible token loss, single point faure
    - without token: Ricart & Agrawala Algorithm
        - mechanism
            - Processes want to enter critical point will broadcast the request(with timestamp). After get permission from everyone else, it can enter
            - When hearing from other's request
                - If I don't mean to enter critical section, I reply OK
                - If I am in critical section, don't reply until exit
                - If I just send a request as well, smaller timestamp wins and get OK response. If i win other request will be handled after critical section

## Communication mechanism in mutual excl
- mEssage passing
- Shared Memory
    - Idea: Processes communicate on a public billboard--"shared variables"
    - Type of shared variables:
        - R-W regs: not atomic, most primitive
        - R-M-W regs: atomic
        - test&set: for binary lock

    - Mutual excl alg impl:

        - test&set
            - Guarantee no deadlock
            - Not guarantee no lockout (suppose no processor occupy forever)
            - idea: each reg represent is the resource is been used
            - #Register = #shared resources
        - R-M-W
            - Guarantee no deadlock and lockout (suppose no processor occupy forever)
            - idea: one register acts as counter to give tickets
            - #Register: 1
        - R-W reg
            - idea: Lamport     Bakery algorithm
                - Flag=True: you are waiting or using the resource. Release the flag when exiting
                - Each time in entry section, Go through the flag bool[] and ticket int[]
                - Set my flag=True, ticket=Max(ticket[])+1
                - Wait until: no one with flag true has ticket number smaller than mine
                - You can entry now
            - #Register: O(2n)

# 23: Replication

## Replicate Data
- Pros:
    - Reliability: protect against corrupted data
    - Performance: can handle more clients
    - Helps data reside close to where it is used (CDN content delivery network 内容分发网络)
    - Enhance scalability
        - Replication distributes the workload across multiple nodes, so more users can be served simultaneously — which means better scalability.
- Cons:
    - Inconsistency
        - When one of the copies of data is changed, the change need to be propagated. Otherwise inconsistency
- Two deployment:
    - Distributed type: put data near the user
    - Local and centralized: server cluster

## Transparency
- client only see logical object, doesn't care what it really is
- You can require from low transparency to high transparency

## Consistency Model
- Consistency model is the protocol between data system and the services (process) that accesses the data


- Data-centric consistency models
    - Each server has a copy of replicated data
    - Different level:
        - Strict: Anything observed should be real ordered physically
        - Weak: Wrong observation are OK. Need synchronization manually 
    - Operation
        - Read: easy and fast
        - Write: need to be propagated to all copies

    - Global ordering:
        - The order of operations should be the same on all (data) replicas
    - Example:
      - Sequential Consistency
          - All processes see operations (on data system) at same row in the same order. 
          - i.e. P1 reads (13.5 then 14 then 14.5) and P2 reads (13.5 then 14.5). It is consistent
          - NB!
              - In the table, order of operations in the same row matter.
              - Operation in different row can shift/slide left and right
      - 'Weak' level Consistency
          - Operations are regard as groups. It's groups that been synchronized
          - Only if manually synchronized each processor will have the same data
          - If not synchronized, and order is permit

- Client-centric consistency models
    - Core idea is to ensure the part of replicas that accessed by a single user is consistent 

- Eventual consistency
    - Only ensure updates will propagate to all replicas Eventually
    - Suitable for High write and low read
    - If you allow updates latency, then it might violate client-centric consistency






# 24: Replication

## Where to store data replicas
- Types:
    - Permanent
    - Server-initiated replicas
    - Client-initiated replicas
- Propagate updates to replicas
    - Notification: Only send notification of updates. Distributed replica pull from other replicas
        - When write operation on data is frequent
    - Send data directly
        - When read from data is frequent
    - Propagate update operations:
        - Less bandwidth

- Push/Pull protocols
    - Push
        - updates sent automatically by server
        - Server maintains the client list
        - Sometimes push fails, client should poll again
    - Pull: update sent only when client asks for it
    - Hybrid approach: lease
        - server promise to push updates until the leas expires (push is stable in the lease)
        - Type to decide expiration
            - Age-based: persistent data doesn't change too much, aka its age is long
            - Renewal-frequency based: More often client request a data, the **longer** expiration should be 
            - State-space overhead lease: high load server provide shorter lease (otherwise the load is overwhelm)
        - Lease and sync
            - Client's clock may be quite slower that server, so it should assume the error is big and renew the lease in advance
    - Epidemic protocol
        - A method for Eventual consistency
        - It propagate the update with minimum number of messages
        - Problem: deleting data might be tricky???

- Primary based protocol
    - Only primary replica can perform Write/read. Variation allows read on other backups
    - Remote write protocol:
        - All write/read request are sent to the primary replica, which will then do the operation locally and then propagate to other replicas
        - Variation:
            - Primary backup protocol: write is centralized and read is distributed
        - Pro and cons:
            - Cons: bad performance since all writes are conduct single point
            - Pros: guarantee sequential consistency
            - Pros: performance can improve using non-blocking write protocol
    - Local write protocol:
        - And server can be primary (transferrable). Write/read on primary replica
        - When R/W request sent to one server, it request the "PRIMARY" label from current primary server. Then do the operation and propagate the updates
        - Variation
            - Distributed read: write is pseudo-centralized and read is distributed. Read operation doesn't request PRIMARY token
        - Problem:
            - Who is the primary, where is the data
            - Solution: dynamic naming

- Replicated write protocols
    - Each replica can perform both Read and Write. no singly point failure
    - Active replication
        - Operations are propagated instead of data
        - "Total ordering" (operation on each replicas have the same order, even though the arriving time isn't consistent)
            - Lamport's clock
            - Sequence: a process that assign ID to updates operations. and propagate the operation
        - Problem: replicated invocation
            - Solution: select a coordinator representing a group of replicas
