---
title: "ContinuationToken | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d4911fc-c6fb-4628-9177-bd723d4d8ebc
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ContinuationToken
A continuation token is used to correlate heterogeneous information within the BAM infrastructure. Consider a business process that constructs the following types of messages:  
  
- Purchase order identified by a purchase order number  
  
- Sales order identified by a sales order number  
  
- Shipping order identified by a shipping order number  
  
  In this process, there are three important identifiers: purchase order ID, sales order ID and shipping order ID. Each of these identifiers signals an important event in the lifetime of the original order, but they cannot be directly correlated. To track events related to a purchase order, the information that is common between the messages must be identified to help the BAM tracking infrastructure accurately correlate the events.  
  
## Format  
 A continuation token consists of an expression element and one or more operations:  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## Remarks  
 The following common operations are not allowed in ContinuationToken expressions:  
  
- And  
  
- Equals  
  
  [Operations section header in WF/WCF should have similar chart and other charts as needed]  
  
## Example  
 In this example, a continuation token for a WF process is retrieved from the workflow by using `GetWorkflowProperty`. Here the developer decided to provide support for continuation in the workflow by using custom code, probably because the process for determining the continuation token involves more than two or three expressions and may rely on external data.  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>ContinuationToken</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
 You may choose to provide similar functionality in your new WF or WCF applications or, if the token is easy to establish using expression operations, you can avoid writing additional code.  
  
 The following example establishes a continuation token for a WCF process by using an **XPath** operation to retrieve the credit card number from the current message and the **constant** and **concatenate** operations to prepend the string "CID_" to the retrieved number:  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CID_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//Purchase/Payment/CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## See Also  
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)