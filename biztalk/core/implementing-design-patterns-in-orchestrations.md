---
title: "Implementing Design Patterns in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aggregator pattern, orchestrations"
  - "Error Handling pattern [orchestrations]"
  - "patterns, orchestrations"
  - "designing, orchestrations"
  - "orchestrations, designing"
  - "Exception Handling and Compensation pattern [orchestrations]"
  - "Parallel Convoy pattern [orchestrations]"
  - "Dynamic Router pattern [orchestrations]"
  - "orchestrations, patterns"
  - "patterns"
  - "Composed Message Processor pattern [orchestrations]"
  - "Suspend with Retry pattern, orchestrations"
  - "Calling Pipelines from Orchestration pattern [orchestrations]"
  - "Message Filter pattern [orchestrations]"
  - "Message Broker pattern [orchestrations]"
  - "Content-Based Router pattern [orchestrations]"
  - "Sequential Convoy pattern [orchestrations]"
  - "Scatter and Gather pattern [orchestrations]"
  - "Splitter pattern, orchestrations"
  - "Message Translator pattern [orchestrations]"
ms.assetid: f62ba955-018a-40e7-b303-497acc906019
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementing Design Patterns in Orchestrations
This section discusses the common patterns of BizTalk Server programming as well as enterprise integration patterns. You can leverage a single pattern or combine multiple patterns to design your business process and then implement the design by using shapes in BizTalk Orchestration Designer.  
  
## Design Patterns  
 The following entries briefly describe each pattern and point to the topics or samples that show how to implement the patterns using BizTalk Orchestration Designer.  
  
### Aggregator  
 Aggregator is the pattern of receiving information from multiple sources and consolidating it into a single message. For an example of this pattern, see Aggregate.odx in [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).  
  
### Calling Pipelines from an Orchestration  
 You can call send and receive pipelines from your orchestrations. This allows the reuse of pipelines and helps maintain the decoupling of an orchestration from the pipeline stages. For an example of this pattern, see Aggregate.odx in [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md). Another example is CMP.odx in [Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md). See also [How to Use Expressions to Execute Pipelines](../core/how-to-use-expressions-to-execute-pipelines.md).  
  
### Composed Message Processor  
 Composed Message Processor is the pattern of processing individual items from an aggregated or batched interchange message. For an example of this pattern, see CMP.odx in [Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md).  
  
### Content-Based Router  
 Content-Based Router is the pattern of determining the recipient of a message based on some part of the message content. For an example of this pattern, see [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md).  
  
### Dynamic Router  
 Dynamic Router is the pattern of determining the destination address as well as the transport protocol based on the result of message processing. You can use a dynamic send port or a **Role Link** shape to implement this pattern. For an example of this pattern, see ReceiveSend.odx in [SendMail](../core/sendmail.md). Another example is SupplierProcess.odx in [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).  
  
### Error Handling  
 BizTalk Server allows you to designate automated handling of messaging failures as an alternative to the default behavior of placing failed messages in the Suspended queue. You can route failed messages to a subscribing port for reporting or processing. For an example of this pattern, see ResubmitLogic.odx in [Error Handling (BizTalk Server Samples Folder)](../core/error-handling-biztalk-server-samples-folder.md).  
  
### Exception Handling and Compensation  
 You can use an exception handler and a **Throw Exception** shape or an **Expression** shape for exception handling. For example, you can place the following code in the **Expression** shape to throw the exception:,  
  
```  
excp = new System.Exception();  
throw(excp);  
```  
  
 You can use a compensation block and a **Compensate** shape to perform the compensation on the transactions that have been committed. For an example of this pattern, see UpdateContact.odx in [Compensation (BizTalk Server Sample)](../core/compensation-biztalk-server-sample.md). Another example is in [Custom Exceptions](../core/custom-exceptions.md).  
  
### Message Broker  
 Message Broker is the pattern of determining the destination of a message and still maintaining control over the message flow. For more, see  [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).  
  
### Message Filter  
 The Message Filter pattern selects messages meeting particular criteria for processing. You can implement this pattern by adding the filter expression to an activated **Receive** shape. For more information, see [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md).  
  
### Message Translator  
 The Message Translator pattern converts a message from one form to another form. You can implement this pattern by using a BizTalk map with a **Transform** shape in an orchestration. For an example of this pattern, see HelloOrchestration.odx in [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md).  
  
### Parallel Convoy  
 The Parallel Convoy pattern enables multiple single items to join together to achieve something that an individual item cannot accomplish by itself. The set of related items can arrive in any order, but BizTalk Server must receive all of them before starting the process. For an example of this pattern, see [http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035).  
  
### Scatter and Gather  
 The Scatter and Gather pattern enables messages to be sent to multiple recipients and messages to be received back from each recipient. You can implement this pattern by using the Splitter pattern and the Aggregator pattern. You use the Aggregator pattern to assemble the results from using the Splitter pattern and put them under a **Parallel Actions** shape. For an example of the Splitter pattern, see SDK sample named Implementing Scatter and Gather Pattern at [http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185).  
  
### Sequential Convoy  
 The Sequential Convoy pattern enables multiple single items to join together to achieve something that an individual item cannot accomplish by itself. A sequential convoy is a set of related items that have a predefined order. Although the items do not have to be exactly the same, BizTalk Server must receive the items in a sequential order. For an example of this pattern, see [http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035).  
  
### Splitter  
 The Splitter pattern takes a single message and splits it into multiple messages.  
  
### Suspend with Retry  
 The Suspend with Retry pattern enables the orchestration to suspend a message when there is an error. The suspension occurs within a loop so that the orchestration suspends, asks for intervention, and then retries the operation a fixed number of times.  
  
## See Also  
 [Designing Orchestration Flow](../core/designing-orchestration-flow.md)