---
description: "Learn more about: CorrelationID"
title: "CorrelationID | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4faf210-7e7f-450d-8bb1-84d3d31c3022
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CorrelationID
The `CorrelationID` element is used to specify a correlation ID for a message.  
  
## Format  
 The `CorrelationID` element consists of an `Expression` element that uses one or more `Operation` elements to specify the string to use as the correlation ID.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## Remarks  
 The following common operations are not allowed in correlation ID expressions:  
  
-   And  
  
-   Equals  
  
## Example  
 The following Workflow Foundation (WF) interceptor sample configuration block uses "OrderNum" to establish a correlation ID. Using the WF and common operations, you can build sophisticated expressions to construct an appropriate correlation ID for your workflow.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>OrderNum</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 For Windows Communication Foundation (WCF) applications, you can use WCF-specific and common operations to construct a correlation ID. The following sample uses the **XPath** operation and XPath to retrieve a credit card number from a message for use as a correlation ID:  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wcf:Operation Name ="XPath">  
      <wcf:Argument>//s:Body/creditCard:CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## See Also  
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)
