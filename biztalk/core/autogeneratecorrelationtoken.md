---
title: "AutoGenerateCorrelationToken | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a24357c9-34e5-4caa-b41c-19551cfe81f9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AutoGenerateCorrelationToken
Automatically generates a correlation token and places it onto the stack.  
  
## Syntax  
  
```  
  
<wcf:Operation Name="AutoGenerateCorrelationToken" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the correlation token.  
  
## Remarks  
 This operation can be used when there is no correlation token present in the message but you still want to correlate the information from a request and a reply. It can be used to correlate a particular request/reply on either the client or the service side.  
  
> [!NOTE]
>  If you want to correlate the data gathered by the request and the reply for both the client and the service (a continuation), you will need to use a data element or elements from your message.  
  
## Example  
 The following example correlation expression relies on the `AutoGenerateCorrelationToken` to generate a correlation token.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>            
    <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)