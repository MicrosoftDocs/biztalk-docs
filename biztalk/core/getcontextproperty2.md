---
description: "Learn how to use the GetContextProperty to push the requested context property onto the stack."
title: "GetContextProperty2"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# GetContextProperty Overview

Pushes the requested context property onto the stack.  
  
## Syntax  
  
```xml  
<wf:Operation Name="GetContextProperty">  
  <wf:Argument>ContextPropertyName</wf:Argument>  
</wf:Operation>  
```  
  
#### Parameters  
 One of the following context property names:  
  
|Context property name|Description|  
|---------------------------|-----------------|  
|EventTime|Current date and time.|  
|InstanceId|Workflow instance ID.|  
  
> [!NOTE]
> The context property names are case-sensitive.  
  
## Pushed Value  
 String containing the requested context property.  
  
## Remarks  
 Time is stored in UTC format inside of the database.  
  
## Example  
 In the following sample, an expression for pulling the **InstanceId** is used inside of a correlationID block to set the correlation ID.  
  
```xml  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 This is a common use of `GetContextProperty`.
