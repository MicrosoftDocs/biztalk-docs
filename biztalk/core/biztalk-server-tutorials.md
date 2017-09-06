---
title: "BizTalk Server Tutorials | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tutorials, getting started"
  - "getting started, tutorials"
ms.assetid: 58019f98-e91a-4705-b689-c269174d6bae
caps.latest.revision: 42
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server Tutorials
Tutorials to learn how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

The BizTalk Server tutorials contain simple scenarios to give new users an experience of using a variety of BizTalk tools while creating compiled, testable integration solutions. For more advanced users, or users who are designing BizTalk solutions, see [Scenarios for Business Solutions](../core/scenarios-for-business-solutions.md).  
  
## Enterprise Application Integration
  
[Tutorial: Enterprise Application Integration](../core/tutorial-1-enterprise-application-integration.md) 

Implement a BizTalk solution that receives inventory replenishment request messages from a warehouse, and evaluates the request messages. If the solution denies a request, then it sends a decline message to the warehouse. If the solution approves a request, then it forwards the message to an Enterprise Resource Planning (ERP) system.  

## Create a Hybrid Application
[Tutorial: Creating a Hybrid Application Using BizTalk Server](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)  

Set up an end-to-end application that uses EDI to generate acknowledgements, Service Bus to receive messages, and then insert data into SQL. 

## Invoke a REST Interface
[Tutorial: Invoking a REST Interface Using BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)  

Uses the WCF-WebHttp adapter to use a REST URL, and then send a response message. 

## Integrate BizTalk with Salesforce
[Tutorial: Integrating BizTalk Server with Salesforce](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)  

Every time a sales opportunity is created in the Salesforce system, Northwind wants its on-premise systems, such as BizTalk Server, to be notified so that other downstream systems can pick up that data and start other relevant processes. 

## Process JSON messages
[Processing JSON messages using BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)  

Set up a BizTalk application that receives a JSON purchase order. In the receive pipeline, a JSON decoder component transforms the JSON message to XML message. Then, uses a map to transform the XML purchase order into an XML invoice. The send pipeline uses a JSON encoder to transform the XML invoice into a JSON invoice, and then sends the message.

## EDI Interface Developer
  [Tutorial: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md)
  
A trading partner sends purchase orders using the ANSI X12 4010 850 transaction set (an 850 message). An internal order system processes purchase orders.

As an interface developer responsible for designing the interface between the 850 message, you receive from your trading partner and your company’s internal Order System. Your trading partner requires a Functional Acknowledgement (997) for each 850 message it sends.


## AS2  
[Tutorial: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)

Set up a solution that receives and sends EDIINT/AS2-encoded messages over an HTTP transport.    


## Do more  
 To learn more about BizTalk Server concepts and architecture, consider the following:  
  
[Get started](../core/getting-started-with-biztalk-server.md)
  
[Plan and architect your BizTalk Server solution](../core/plan-and-architect-your-biztalk-server-solution.md)