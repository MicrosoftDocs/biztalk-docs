---
title: "Message Queuing Queues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [MSMQ adapters], queue paths"
  - "naming conventions, MSMQ adapters"
  - "configuring [MSMQ adapters], naming conventions"
  - "messages, queuing"
  - "MSMQ adapters, troubleshooting"
  - "MSMQ adapters, message queues"
  - "configuring [MSMQ adapters], troubleshooting"
  - "troubleshooting, queue paths [MSMQ adapters]"
  - "naming conventions, queue paths [MSMQ adapters]"
  - "configuring [MSMQ adapters], message queues"
ms.assetid: b802348e-8543-4b06-a6e4-149b86139fb1
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Queuing Queues
This section describes how to specify Microsoft Message Queuing (also known as MSMQ) queues when you use the MSMQ adapter. It describes the conventions for specifying paths and also describes the role that format names play in translating paths into queue designations.  
  
## Queue Path Naming Conventions  
 If the queue name refers to a path, use the naming conventions in the following table.  
  
|**Queue type**|**Syntax for path**|  
|--------------------|-------------------------|  
|Public queue|*Computername*\QueueName|  
|Private queue|*Computername*\Private$\QueueName|  
|Journal queue|*Computername*\QueueName\Journal$|  
|Computer journal queue **Note:**  Use for receive queue only.|*Computername*\Journal$|  
|Computer dead-letter queue **Note:**  Use for receive queue only.|*Computername*\Deadletter$|  
|Computer transaction dead-letter queue **Note:**  Use for receive queue only.|*Computername*\XactDeadletter$|  
  
> [!NOTE]
>  The path of the queue must be unique.  
  
 If the queue name refers to a format name, it takes the form of a string that indicates whether a queue is public or private, followed by a generated GUID for the queue and other identifiers as needed. Use the naming conventions in the following table.  
  
|**Format type**|**Syntax for format name**|  
|---------------------|--------------------------------|  
|Public|*FormatName*:Public=QueueGUID|  
|Direct|*FormatName*:DIRECT=SPX:NetworkNumber:HostNumber\QueueName<br /><br /> *FormatName*: DIRECT=TCP:IPAddress\QueueName<br /><br /> *FormatName*: DIRECT=OS:ComputerName\QueueName|  
  
 If the send port queue path is a distribution list, then the queue path syntax is:  
  
 DL=DistributionListGUID  
  
 If the send or receive queue path is an HTTP or HTTPS URL, then the syntax is:  
  
 FormatName:DIRECT=http://\<client name>/msmq/\<queue name>  
  
 FormatName:DIRECT=https://\<client name>/msmq/\<queue name>  
  
> [!NOTE]
>  "msmq" is the virtual folder that Message Queuing creates in Internet Information Services (IIS).  
  
> [!NOTE]
>  You can only use HTTP to send messages. You cannot read messages in a queue on a remote computer if the queue is opened using an HTTP direct format name. However, you can still receive SOAP (formatted) messages from a remote queue by using the private or public queue path without HTTP.  
  
 If the queue name refers to a descriptive text label that the administrator specified for the queue, then the syntax of the queue path referring to this label is:  
  
 LABEL:MyQueue  
  
> [!NOTE]
>  Labels are not always unique. Therefore, you will receive an error if a name conflict exists when you try to connect to a specific queue by using its label.  
  
> [!NOTE]
>  The label is a required transport field for the adapter.  
  
## Role of the Format Name  
 Message Queuing uses the format name to identify a queue and to determine how to access it. Message Queuing assigns the format name to the queue.  
  
 When you specify a queue using the path name syntax, for example myMachine\myQueue, Message Queuing looks up the path to find the associated format name. Message Queuing then uses that format name to access the queue. When you specify the format name, Message Queuing uses the format name you use.  
  
 For more information about format names, see "MessageQueue.FormatName Property" in .NET Framework Class Library Help.  
  
## Troubleshooting Queue Paths  
  
-   An exception occurs if the syntax of the provided queue path does not match one of the formats described earlier in "Queue Path Naming Conventions."  
  
-   The following are not valid characters for computer names in the queue path:  
  
     \ ; , + "  
  
     An exception occurs if the computer name is a number. For example: 234\private$\queue.  
  
-   For a computer dead-letter queue, computer journal queue, and computer transaction dead-letter queue, an exception occurs if the user specifies any one of the system queues as the destination queue for send.  
  
-   **System.Messaging.MessageQueue.Exists** does not work for remote queues. For more information, see "MessageQueue.Exists Method" in .NET Framework Class Library Help.  
  
## See Also  
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)