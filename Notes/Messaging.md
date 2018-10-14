# Messaging

A method of communication between applications. It enables loose coupling among applications by communicating asynchronously. More reliable as sender and receiver don't have to be running at the same time.

## Components
 - Message producer & consume
 - Queue
 - Topic 
 - Broker

## Channels 
 - Point-to-Point Channel
 - Publish-Subcriber Channel
 - Dead-letter Queue

## Message Persistence
 - In memory queue
 - Persistent Queue
 - Transaction support
 - Time to live setting

## Major messaging protocols
 - Java Messaging Service(JMS)
 - Advanced Messaging Queuing Protocol (AMQP)
 - Simple Text Oriented Messaging Protocol (STOMP)
 - MQTT

#### STOMP
 - Similar to HTTP.
 - Interoperable wire format
 - Very easy to implement & language agnostic like REST

## Broker-based Architecture
 - Classical star architecture
 - Every app is connected to central broker
 - No point-to-point direct communication between apps
 - All communication passes through broker
 - Apps don't need to know the location of other apps. They only require broker address
 - Broker does the routing of messages based upon queue name, topic and message properties.
 - Sender does not have to remain running for receiver to receive the message. It can send the message and terminate and the receiver will receive the message when it starts running.
 - Drawback is that it requires excessive amount of network communication
 - Broker is a single point of failure and a bottleneck for compelete architecture.

## Broker-less architecture
 - Applications send messages to each other directly
 - No broker is involved
 - Applications have to know the network address of the application they want to send the message to.
 - Ideal for low latency app or apps with high transaction rate.
 - No single point of failure or bottleneck
 - Faster response time
 - No location transparency
 - Less fault tolerant
 - Lower uptime as all the apps have to be running for system to be up

## Broker-less with a directory service architecture
 - Location transparency as directory service hides the physical location of applications
 - Better manageability of the system
 - Message transfer is still done by applications
 - High performance and manageabilty at same time