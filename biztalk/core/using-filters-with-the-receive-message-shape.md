---
title: "Using Filters With the Receive Message Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filters, receive messages"
  - "messages, filters"
ms.assetid: 5310039b-6719-4971-933a-2da0573fb5e7
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Filters With the Receive Message Shape
A filter expression is an optional parameter that can be applied to an orchestration receive shape that specifies a value of True for the Activate property. If a filter expression is specified then the orchestration will only be activated if an incoming message matches the condition(s) specified in the filter expression. If no filter expression is specified then any incoming message that the orchestration subscribes to will activate the orchestration.  
  
 To create a filter expression, you compare a property of an incoming message on the left side of the expression with a constant on the right side of the expression. You can also create compound expressions by applying the AND and OR operators to two or more expressions. You can also leave blank the filter expression, in which case all messages will be accepted.  
  
 A filter expression might look like the following:  
  
```  
InvoiceSchema.Quantity >= 1000  
```  
  
 In this example, an incoming message is presented to the orchestration. The orchestration has an activation **Receive** shape (the **Activation** property is set to **True** so that receipt of a certain message will cause the orchestration to be run) with the preceding filter expression applied to it. The incoming message is expected to have property called Quantity in the namespace **InvoiceSchema**. The orchestration accepts only invoices for 1000 or more items, so the runtime engine checks the incoming message before it runs.  
  
 The following table shows operators that you can use in filter expressions.  
  
|Operator|Description|Example|  
|--------------|-----------------|-------------|  
|==|equal to|ReqMsg(Total) == 100|  
|!=|not equal to|ReqMsg(Total) != 100|  
|<|less than|ReqMsg(Total) \< 100|  
|>|greater than|ReqMsg(Total) > 100|  
|<=|less than or equal to|ReqMsg(Total) \<= 100|  
|>=|greater than or equal to|ReqMsg(Total) >= 100|  
|exists|exists|ReqMsg(Description) exists|  
  
> [!NOTE]
>  String values in filter expressions are enclosed in quotation marks, for example: ReqMsg(Description) = "Purchase Order Status". You cannot use a character value in a filter expression.  
  
> [!NOTE]
>  If your activate receive is associated with a direct-bound port, and you subsequently send a message of the same type with the same value for the property tested in your filter, you will create an infinite loop. The message will go to the MessageBox, where it will be picked up again because it matches the filter criteria. To avoid this, you should either filter on a different property, send a message of a different type, or be sure to change the value of the property before sending out a message of the same type.  
  
## See Also  
 [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md)   
 [Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md)   
 [Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md)   
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)