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




##Java Testing





#Javascript


## Javascript Testing

