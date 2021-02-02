---
description: "Learn more about: GetContextProperty"
title: "GetContextProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2554a210-cfb4-4b63-9afa-ffe2a853ba7b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetContextProperty
Pushes the requested context property onto the stack.  
  
## Syntax  
  
```  
  
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
>  The context property names are case-sensitive.  
  
## Pushed Value  
 String containing the requested context property.  
  
## Remarks  
 Time is stored in UTC format inside of the database.  
  
## Example  
 In the following sample, an expression for pulling the **InstanceId** is used inside of a correlationID block to set the correlation ID.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 This is a common use of `GetContextProperty`.
