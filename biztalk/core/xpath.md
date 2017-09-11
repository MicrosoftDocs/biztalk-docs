---
title: "XPath | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 444b5eb9-0c00-4225-918e-b973532c67d0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XPath
Pushes the value indicated by an XPath statement.  
  
## Syntax  
  
```  
  
<wcf:Operation Name="XPath">  
  <wcf:Argument>//po:POID</wcf:Argument>  
</wcf:Operation>  
```  
  
#### Parameters  
 Valid XPath statement.  
  
## Pushed Value  
 String value of the result found by executing the XPath statement.  
  
## Remarks  
 You must use a valid XPath statement.  
  
 In the case of multiple matches, only the first match is used.  
  
## Example  
 The following example expression constructs a correlation value by concatenating a constant "C_" with the purchase order ID from the current message. The purchase order ID is retrieved by using the XPath operation.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>C_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//po:POID</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)