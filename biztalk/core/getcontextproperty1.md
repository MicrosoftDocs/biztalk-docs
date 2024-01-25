---
description: "Learn about the GetContextProperty that pushes the requested context property onto the stack."
title: "GetContextProperty1"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetContextProperty

Pushes the requested context property onto the stack.  
  
## Syntax  
  
```xml  
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
> The context property names are case-sensitive.  
  
## Pushed Value  
 String containing the requested context property.  
  
## Remarks  
 Time is stored in UTC format inside of the database.  
  
## Example
  
In the following sample update expression, the approval date is retrieved by retrieving the event time of the current event.  
  
```xml  
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

- [Operations in Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)
