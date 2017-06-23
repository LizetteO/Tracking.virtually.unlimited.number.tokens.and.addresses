---

title: Efficient garbage collection and exception handling in a hardware accelerated transactional memory system
abstract: Handling garbage collection and exceptions in hardware assisted transactions. Embodiments are practiced in a computing environment including a hardware assisted transaction system. Embodiments includes acts for writing to a card table outside of a transaction; handling garbage collection compaction occurring when a hardware transaction is active by using a common global variable and instructing one or more agents to write to the common global variable any time an operation is performed which may change an object's virtual address; acts for managing a thread-local allocation context; acts for handling exceptions while in a hardware assisted transaction. A method includes beginning a hardware assisted transaction, raising an exception while in the hardware assisted transaction, including creating an exception object, determining that the transaction should be rolled back, and as a result of determining that the transaction should be rolled back, marshaling the exception object out of the hardware assisted transaction.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08402218&OS=08402218&RS=08402218
owner: Microsoft Corporation
number: 08402218
owner_city: Redmond
owner_country: US
publication_date: 20091215
---
