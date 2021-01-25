---
description: "Learn more about: TIBCO Rendezvous Concepts"
title: "TIBCO Rendezvous concepts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36060091-57dc-4125-8dca-23058d813deb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TIBCO Rendezvous Concepts

## Concepts explained
The following table describes some of the features and concepts in TIBCO Rendezvous.  
  
|Concept|Definition|  
|-------------|----------------|  
|**Messages**|Carry data among program processes or threads. Messages contain self-describing data fields. Programs can manipulate message fields, send messages, and receive messages.|  
|**Events**|Create event objects to register interest in significant conditions. For example, dispatching a listener event notifies the program that a message has arrived; dispatching a timer event notifies the program that its interval has elapsed.<br /><br /> Programs define event callback functions to process events.|  
|**Subjects**|Messages are associated with a logical name (subject). Programs listen for a particular subject, or publish messages under a specific subject.|  
|**Transports**|Objects that define delivery scope, mechanism, and protocols.|  
|**Batch Mode**|TIBCO Rendezvous transport objects support a batch mode for publishing messages. <br />Default mode is: Send messages as soon as possible. Timer Batch mode is: Accumulate messages and send when buffer is full or timer interval expires.|  
|**Queue**|Programs create event queues to organize events. A queue holds a sequence of event objects that are ready to be processed.|  
|**Queue Group**|Customizes event processing by combining queues (using different priorities).|  
|**Certified Message Delivery**|Confirms delivery of each message to each registered recipient. Delivers messages despite process termination and restart by using file-based ledgers.<br /><br /> Certified delivery assures programs that every certified message reaches each intended recipient—in the order sent. When delivery is not possible, both sending and listening programs receive explicit information about each undelivered message.<br /><br /> Programs determine an explicit time limit for each message.<br /><br /> After a program sends a certified message, TIBCO Rendezvous software continues delivery attempts until delivery succeeds, or until the message’s time limit expires.<br /><br /> TIBCO Rendezvous certified delivery software presents advisory messages to inform programs of every significant event relating to delivery.<br /><br /> TIBCO Rendezvous certified delivery software records the status of each message in a ledger. Programs that require certification only for the duration of the program process should use a process-based ledger. Programs that require certification that transcends process termination and program restart use a file-based ledger.<br /><br /> When certified delivery is not allowed, delivery conditions decrease to the standard TIBCO Rendezvous reliable delivery semantics.|  
|**Distributed Queue Daemons**|Distribute a service over several processes.<br /><br /> The TIBCO Rendezvous daemon completes the information pathway between TIBCO Rendezvous program processes across the network. Programs try to connect to a TIBCO Rendezvous daemon process. If a local daemon process is not yet running, the program starts one automatically and connects to it. The TIBCO Rendezvous daemon arranges the details of data transport, packet ordering, receipt acknowledgement, retransmission requests, and dispatching information to the correct program processes. The daemon hides all these details from TIBCO Rendezvous programs. The TIBCO Rendezvous daemon is almost invisible to the programs that depend on it. Programs send and receive information using TIBCO Rendezvous communications calls, and the TIBCO Rendezvous daemon does the work of getting information to the appropriate place.<br /><br /> The daemon does the following:<br /><br /> -   Transmits outbound messages from program processes to the network.<br />-   Delivers inbound messages from the network to program processes.<br />-   Filters subject-addressed messages.<br />-   Shields programs from operating system idiosyncrasies, such as low-level sockets.|  
|**Security**|TIBCO Rendezvous supports authentication based on certificates or (user, password).|  
|**Virtual Circuits**|Feature Rendezvous communication between two terminals over an exclusive and continuous monitored connection.|  
|**Direct Communication**|Point-to-point communications without intermediary Rendezvous daemon processes.|  
  
## See Also  
 [Messages in BizTalk Adapter for TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)
