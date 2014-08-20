technical-interview-questions
=============================

Technical Interview Questions Projekt Contains fullstack interveiw questions for enterprise portal development including backend and frontend questions

#Java Questions

- Describe Java Messaging Service (JMS) messaging modes

Synchronous: In this mode a sender component sends a message via message-oriented middleware (MOM) message queue to atnoher component and waits for answer to proceed further. This is similar to blocking IO.

Asynchronous: In this mode a sender component sends a message to another component via MOM message queue and continues processin further without waiting for an answer. Async. mode is desireable in case of high volume processing. 

- Describe JMS Messaging models

publish and subscribe: (aka. one-to-many ) One producer sends a message to many consumers through a virtial channel called a *topic*. Consumers can subscribe to a *topic*. Every consumers recieves a copy of each message. 

point to point: (aka. one-to-one ) it is possible to send messages async. and sync. via virtual channels called *queue*. A queue can have multiple reciever but only one reciever gets the message. p2p guarantees that only one consumer processes each message.  


- Describe Message Driven Bean (MDB)

Message driven beans are transaction aware, stateless server side components for processing async. JMS Messages. Advantage of MDB over traditional JMS clients is concurency, transaction management etc. which are managed by the container.MDBs "listen" on a specific JMS destination, which can either be a queue or a topic.

Use message driven beans for following use cases

1. long-running operations to be processed async.
2. when some resources can not be avaiable
3. parallel processing
4. third party integration

- Describe web services 

There are to kinds of webservices as xml webservices and RESTful webservices.
In both cases Singletons and stateless session beans can be used implement webservices. Adding @WebService will expose all public methods as webservice.

XML Webservices (jax-ws): that is java api for xml webservices SOAP(Simple object access protocol). Metro is reference implementation. 

RESTful webservices (jax-rs): that is java api for RESTful webservices. Jersey is reference implementation. REST is Representational State Transfer.

- Describe transaction isolation levels

- Describe optimistic and pessimistic locking

If you have a multiuser portal where users can change other users data as the following example, you need to use optimistic or pesimistic locking. (ref:http://bit.ly/1q0FcVG)

1. User A reads a record
2. User B reads the same record
3. User A updates that record
4. User B updates the same record

User B2 has now over-written the changes that User A made. They are completely gone, as if they never happened. 
This is called a 'lost update'.

Pessimisic Locking: Locks the records when it is read e.g. by using (FOR UPDATE)

1. User A reads a record *and locks it* by putting an exclusive lock on the record (FOR UPDATE clause)
2. User B attempts to read *and lock* the same record, but must now wait behind User A
3. User A updates the record (and, of course, commits)
4. User B can now read the record *with the changes that User A made*
5. User B updates the record complete with the changes from User A

The lost update problem is solved. The problem with this approach is concurrency. User a is locking a record that they might not ever update. User B cannot even read the record because they want an exclusive lock when reading as well. This approach requires far too much exclusive locking, and the locks live far too long (often across user control - an *absolute* no-no). This approach is almost *never* implemented.

Optimistic Locking:  Optimistic locking does not use exclusive locks when reading. Instead, a check is made during the update to make sure that the record has not been changed since it was read. This can be done by checking a version field (timestamp or number) in the table.



- Describe new features and improvements in java 6EE

1. Contexts and dependency injection (CDI) Looser coupling, scoping for components.
2. Simplified packaging (ejbs in war file)
3. No interface (local or remote)
4. Async. method invodation on session bean methods.
5. EJB Lite
6. JSF2
7. Singileton beans

- Describe statefull session bean 

SFSB represents state of a specific client in its instance variables. the session ends when client terminates or removes the bean. Use it in following use cases:

1. bean state must represent state of a specific client 
2. bean must hold information about the client

- Describe stateless session beans 

SLSB beans instance variables may contain state specific to a client but only to the end of a method. when the method is finshed, the client specific state should not be retained. Use it in following use cases:

1. bean state has not data to a specific client 
2. to implement a webservice endpoint

- Describe Entity Beans

Entity bean classes are discouraged since java EE 5 and replaced by JPA Entity classes.
JPA is introduced in java EE 5 Specification

- What is DI and CDI 

DI (dependency injection) is generatel term. You can use in unit tests and in other frameworks such as Google Guice, Spring ...

CDI (Context Dependency injection) on the other hand combines this technology and introduces life cycle. you can compbine all those technologies with lifecycle mappings e.g. spring mvc with jpa etc..

##Java Testing





#Javascript


## Javascript Testing

