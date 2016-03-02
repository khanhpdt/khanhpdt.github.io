---
layout: post
title: Software Architectures
category: architectures
---
# The Java EE Architect's Handbook, 2nd edition

## Chapter 4: Designing external application interfaces

- External application interfaces define how our application interacts with the external ones.

- Strategies to fetch external data
  - Read the database of the external application directly
  - Read the operational data store created from the external data. The data in these data stores can also be in a vendor-independent format so that changing the data stores will not affect our application.
  - Use JAX-WS web services supported by the external applications. The most important advantage of using web services is that it is platform-independent. Two applications written in different technologies can still talk to each other via web services. One disadvantage of JAX-WS is that it is not optimized to receive big data.

    > It is usually advisable to segregate code consuming or publishing web services from the rest of your application.

  - Use JAX-RS web services. One disadvantage is that it does not hava a standard specification yet, as opposed to JAX-WS whose specification can be written in WSDL files.
  - Use messaging services, which are asynchronous communication methods. These services can be implemented by message-driven beans in Java EE. Main advantage is the asynchronousity, which can provide guaranteeed dilivery because we can retry if the calls were failed.
  - Use EJBs, but this limits the participants to use Java.

- Common mistakes
  - Use database or file system as message broker. This means that the messages are put into the database or file system, and then there is another process which will read these messages from the database or file system and handle them.
  - Use asynchronous methods when their responses are required
  - Not tested on production environment
