---
title: "Subscription Details Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.subscriptiondetails"
ms.assetid: 22ed4779-bb6c-473e-805c-18e82361bb98
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Subscription Details Properties Dialog Box
The Subscription Details window enables you to examine subscriptions in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Type**|Displays whether the selected subscription is an instance subscription or an activation subscription. Activation subscriptions start new instances of a service, such as an orchestration or a send port. Instance subscriptions are created by service instances already running. These are created at runtime on the MessageBox on which the service instance exists and then copied to the master MessageBox.|  
|**Priority**|Displays the order in which messages are retrieved from the queue. When a message is routed by way of a given subscription, the message reference, which is put in the application's queue, is given the priority of the subscribing subscription. Messages with higher priority are dequeued first.|  
|**State**|Displays the current state of the selected subscription. Subscription states displayed may be Started, Stopped, or Disabled.|  
|**Ordered Delivery**|Specifies whether Ordered Delivery was selected for a send port or orchestration receive port. When **Ordered Delivery** is True, messages must be processed through the port in a specified order. **Ordered Delivery** is important for messages that must be processed as a convoy. Ordered Delivery is false in all other circumstances.|  
|**Request/Response**|Displays whether the receive port is a request-response port. When **Request/Response** is **True**, messages routed to this subscription generate a response message. This property is set by Solicit-Response send ports and by Request-Response orchestration receive ports.|  
|**Creation Time**|Displays the time when the subscription was created.|  
|**Valid From**|Displays the absolute time, set by the messaging engine, before which the engine cannot read and process a message. This value is copied into the queue table from which the engine reads messages. Two common cases where this value is applied are retries on send ports and delay shapes in orchestrations. You do not set this property anywhere in BizTalk Server, and it will nearly always be zero.|  
|**Start Window**|Displays the time the port begins to transmit. This property applies to ports configured with a service window.|  
|**End Window**|Displays the time the port ceases to transmit. This property applies to ports configured with a service window.|  
|**Subscription ID**|Displays the unique ID of the subscription.|  
|**Service class**|Displays the kind of subscription selected.|  
|**Service name**|Displays the name of the service, such as an orchestration name or a port name.|  
  
## Expression Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Property**|Displays the name of the context property used for subscription matching.|  
|**Operator**|Displays the mathematical operator used in the expression.|  
|**Value**|Displays the value of the context property used for subscription matching.|  
|**Group by**|Displays a group of expressions that are connected through the AND operator during the subscription matching process. All expressions connected by AND must be true for a subscription to match the expression.|  
  
## See Also  
 [Service Instance and Message Instance States](../core/service-instance-and-message-instance-states.md)