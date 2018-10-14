# Consistency

## ACID Properties
    - Atomicity - Transaction should be complete
    - Consistency - Transaction bring DB from one valid state to another
    - Isolation - Each transaction behaves in isolation. No collision
    - Durability -  Commited transactions would remain on DB even in case of crash or power failures

## BASE(Basically available) Properties 
	- Soft state or eventual consistency
	- BASE accepts that DB consistency would be in a state of flux
	- Faster than ACID

*Consistency state is a constraint on system state observable by applications.*

#### Strict Consistency
Each operation is stamped with a timestamp. Each READ by any of the node gets the latest WRITE value. Example: Atomic read-write

##### Sequential Consistency
No timestamp available. Gets the closest value. Each node sees the WRITE operation on same memory in same order although order of execution may be different.

#### Eventual Consistency
If no new updates are made to the data, then eventually all access to the data will return the most updated one. It supports disconnected operations i.e. Rather than returning nothing on READ, it can return a STALE value or rather than rejecting a WRITE if main DB is down, it saves it somewhere else and sync-up later. It is about trading consistency for availability. 

## CAP Theoram (Choose any two)

#### Consistency
All nodes see the same data at same time

#### Availabilty
Every request receives a response

#### Tolerance to network partitions
System continues to operate despite messages cannot flow through between nodes.

## Fault-tolerant Systems
	- Also known as graceful degradation or high-availability system
	- A fault-tolerant system can continue operating properly in event of failure of some of its components
	- No single point of failure
	- Fault isolation to failing component
	- Rollback to previous working version
	- Fault containment to prevent propogation of failure
	- Failures are detected using heartbeats
	- Using a fixed timeouts for a heartbeat can cause a false alarm in case of high network traffic
	- Supports multiple identical instances and switches back to the backup instamce ion case of a failure (*Fault tolerance by redundancy*)
	- Provides multiple identical instances of the same system or subsystem and forward requests to all of them in parallel (*Fault-tolerance by replication*)
	- Key replication patterns are: 
		- Consistent Hashing
		- Quoram-based replication
	- Provide multiple implementations of same specifications and use them like replicated systems(Fault tolerance by diversity)

#### Bulkhead
Goal is to stay afloat even if part of the system has been damaged via redundancy. The system can also be partitioned into multiple servers handling different functionality.

## Circuit Breaker
	- A design pattern to detect failures and prevent cascading failures.
	- Can be used to check availability of external service.
	- States
		- Open
		- Closed 
		- Half Open
	- Configurations
		- Max failures count
		- Call timeout
		- Reset timeout

#### Flow of a circuit breaker
	- Closed: When the service is functioning in a normal manner, the circuit breaker remains in closed state and all the request calls pass through to the service. 
	- Open: When number of failures go above a predetermined threshold, the breakers trips and come in open state. From now on, the circuit breaker returns an error response without actually passing the request to the service.
	- Half-Open: After a certain timeout, the breaker comes in half-open state for testing the running condition of the service. If the request fails again, then the breaker goes back to open state. If the request is successfull the breaker goes in closed state and the normal request flow is resumed.