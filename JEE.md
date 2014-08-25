#Java EE Questions

## Describe Java Messaging Service (JMS) messaging modes

Synchronous: In this mode a sender component sends a message via message-oriented middleware (MOM) message queue to atnoher component and waits for answer to proceed further. This is similar to blocking IO.

Asynchronous: In this mode a sender component sends a message to another component via MOM message queue and continues processin further without waiting for an answer. Async. mode is desireable in case of high volume processing. 

## Describe JMS Messaging models

publish and subscribe: (aka. one-to-many ) One producer sends a message to many consumers through a virtial channel called a *topic*. Consumers can subscribe to a *topic*. Every consumers recieves a copy of each message. 

point to point: (aka. one-to-one ) it is possible to send messages async. and sync. via virtual channels called *queue*. A queue can have multiple reciever but only one reciever gets the message. p2p guarantees that only one consumer processes each message.  


## Describe Message Driven Bean (MDB)

Message driven beans are transaction aware, stateless server side components for processing async. JMS Messages. Advantage of MDB over traditional JMS clients is concurency, transaction management etc. which are managed by the container.MDBs "listen" on a specific JMS destination, which can either be a queue or a topic.

Use message driven beans for following use cases

1. long-running operations to be processed async.
2. when some resources can not be avaiable
3. parallel processing
4. third party integration

## Describe web services 

There are to kinds of webservices as xml webservices and RESTful webservices.
In both cases Singletons and stateless session beans can be used implement webservices. Adding @WebService will expose all public methods as webservice.

XML Webservices (jax-ws): that is java api for xml webservices SOAP(Simple object access protocol). Metro is reference implementation. 

RESTful webservices (jax-rs): that is java api for RESTful webservices. Jersey is reference implementation. REST is Representational State Transfer.

## Describe optimistic and pessimistic locking

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

The lost update problem is solved. The problem with this approach is concurrency. User a is locking a record that they might not ever update. User B cannot even read the record because they want an exclusive lock when reading as well. This approach requires far too much exclusive locking, and the locks live far too long (often across user control ## an *absolute* no-no). This approach is almost *never* implemented.

Optimistic Locking:  Optimistic locking does not use exclusive locks when reading. Instead, a check is made during the update to make sure that the record has not been changed since it was read. This can be done by checking a version field (timestamp or number) in the table.

## Describe java.lang.OutOfMemoryError : java heap space

Java memory is seperated into two different regions: heap and permgen space. They can be set at application startups by -Xmx and -XX:MaxPermSize parameters. e.g. -Xmx1024m or -Xmx1g. 
java.lang.OutOfMemoryError will be triggered when you add more that data to the heapspace that is larger than JVM can accomodate in the heap java space.

Cause of OutOfMemoryError can be spikes in usage/data volume, or memory leaks. It is possible to increase heap size to solve the problem. But to solve it permanently you need can analyse the problem by using Debuggers, profilers, heap dump analyzers. 
But whenever you wish to check whether your application is free from memory leaks and runs on optimal heap configuration.
Object etc are stored in heap space and valid for application. On the other hand stack space is only for method level. Each tread has its own stack. 
e.g.: IBM HeapAnalyzer , YourKit profiler, jvisualvm:take heap dump, eclipse.org/mat/ Memory Analyzer Tool, jmap: take heap dump. 

## Which IDEs have you used?

jetbrains, eclipse, netbeans, jetbrains webstrom

## Describe new features and improvements in java 6EE

1. Contexts and dependency injection (CDI) Looser coupling, scoping for components.
2. Simplified packaging (ejbs in war file)
3. No interface (local or remote)
4. Async. method invodation on session bean methods.
5. EJB Lite
6. JSF2
7. Singileton beans

## Describe statefull session bean 

SFSB represents state of a specific client in its instance variables. the session ends when client terminates or removes the bean. Use it in following use cases:

1. bean state must represent state of a specific client 
2. bean must hold information about the client

## Describe stateless session beans 

SLSB beans instance variables may contain state specific to a client but only to the end of a method. when the method is finshed, the client specific state should not be retained. Use it in following use cases:

1. bean state has not data to a specific client 
2. to implement a webservice endpoint

## Describe Entity Beans

Entity bean classes are discouraged since java EE 5 and replaced by JPA Entity classes.
JPA is introduced in java EE 5 Specification

## What is DI and CDI 

DI (dependency injection) is generatel term. You can use in unit tests and in other frameworks such as Google Guice, Spring ...

CDI (Context Dependency injection) on the other hand combines this technology and introduces life cycle. you can compbine all those technologies with lifecycle mappings e.g. spring mvc with jpa etc..

## Describe JAXB API

JAXB(Java Architecture for XML Bindings) provides higher level of abstraction than SAX or DOM.
JAXB is based on annotations e.g.  @XmlRootElement, @XmlType.


## Compare SAX, StAX, DOM APIs


StAX and SAX donot have xpath capability but they have low CPU usage.
SAX is using push model. SAX is readonly but provides Schema Validation. 
  
    SAX Parser --> Handler

StAX is using pull model. StAX allows writing xml files but donot have schema validation.


    Handler --> StAX Parser

DOM is in memory.


## Describe push and pull parsing

Push parser: events are generated by the API in the form of callbacks such as startElement(), endElement(). Parser calls callbacks as events occur. Programmers can not get a specific element.

Pull parsers: Events are generated when we call an API method such as event.next();


## Describe Transaction Isolation Levels

Levels are defined in terms of three phenomena that are either permitted or not at a given isolation level: 

Dirty read: It is permitted to read uncommitted, or dirty , data. Data integrity is compromised, foreign keys are violated, and unique constraints are ignored.

Nonrepeatable read: Data is not the same between two read at time1 and time2.

Phanthom read: Similar to nonrepeatble read but in that case num of rows are different at time1 and time2.


    Isolation Level	   Dirty Read	Nonrepeatable Read	  Phantom Read
    READ UNCOMMITTED   Permitted	Permitted	          Permitted
    READ COMMITTED	   --	        Permitted	          Permitted
    REPEATABLE READ	   --	        --	                  Permitted
    SERIALIZABLE	   --	        --	                  --

## Which JSF Frameworks are there? 

RichFace, PrimeFace, IceFaces

## Describe 6 JSP Lifecycles 

1. Restore View: JSF builds the view, wires event handlers and validators to UI components and saves the view in the FacesContext instance. The FacesContext instance will now contains all the information required to process a request.
2. Aply request values: extract new value from the request parameters
3. Process validation:  JSF processes all validators registered on component tree. It  examines the component attribute rules for the validation and compares these rules to the local value stored for the component.
4. Update model values: JSF checks that the data is valid,
5. Invoke application: JSF handles any application-level events, such as submitting a form / linking to another page.
6. Render response: JSF asks container/application server to render the page if the application is using JSP pages

## Which persistance API have you used?

JDBC,JPA, Hiberate, OpenJPA, EclipseLink ....

## What are the differences between those persistance APIs?

JDBC is good if you want to use legacy code but it is not good for programming perpective. 
Hibernate is easy to program provides mapping.

#
## Descibe new features in JEE6


JPA2 (JPQL, Criteria API),
JSF2,
EJB 3.1 (No-interface view, singletons, asynchronous session bean invocation, EJB Lite)
CDI (Contexts Dependency Injection),
Bean Validation,
JAX-RS,

Obsolete Patterns:

Service Locator - Builder [Use dependency Injection]
Business Delegate - Delegator [Use java interfaces instead of EJB's remote interfaces]
Transfer Object [We can now use POJO for entities] 

Pattern

BCE, Strategy, Factory, Proxy (Interceptor), Observer (Event+fire, @Asynchronous handle(@Observes))
