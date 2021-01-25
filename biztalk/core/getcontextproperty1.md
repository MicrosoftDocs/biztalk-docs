---
description: "Learn more about: GetContextProperty"
title: "GetContextProperty1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8867c29-63de-4a13-9ef9-8c6ab8ea3443
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetContextProperty
Pushes the requested context property onto the stack.  
  
## Syntax  
  
```  
  
<wcf:Operation Name ="GetContextProperty">  
  <wcf:Argument>EventTime</wcf:Argument>  
</wcf:Operation>  
```  
  
#### Parameters  
 One of the following context property names:  
  
|Context property name|Description|  
|---------------------------|-----------------|  
|EventTime|Current date and time.|  
|SessionId|Workflow session id.|  
  
> [!NOTE]
>  The context property names are case-sensitive.  
  
## Pushed Value  
 String containing the requested context property.  
  
## Remarks  
 Time is stored in UTC format inside of the database.  
  
## Example  
 In the following sample update expression, the approval date is retrieved by retrieving the event time of the current event.  
  
```  
<ic:Update DataItemName ="Approval Date" Type ="DATETIME">  
  <ic:Expression>  
    <wcf:Operation Name ="GetContextProperty">  
      <wcf:Argument>EventTime</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
 This is a common use of `GetContextProperty`.  
  
## See Also  
 [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)
