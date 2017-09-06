---
title: "GetActivityType | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65a5aae3-9688-4c49-a78e-1d9c1cc85fea
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetActivityType
Pushes the name of the current activity type onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetActivityType" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current activity type in assembly-qualified class name format.  
  
## Remarks  
 The `GetActivityType` operation retrieves the current activity type and places it on the stack in assembly-qualified class name format:  
  
```  
TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08, processorArchitecture=MSIL  
```  
  
 When comparing, you can specify as much of the type as necessary to satisfy your specific search needs. For example, you might compare the result of GetActivityType with the constant:  
  
 TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0  
  
 This is less restrictive than the assembly-qualified class name format.  
  
## Special Filter Behavior  
 When this operation is performed inside of a filter, derived activities are always matched as well.  
  
## Example  
 The following sample contains an event filter expression that will evaluate to `true` for `System.Workflow.ComponentModel.Activity` instances and any instances from classes that derive from `System.Workflow.ComponentModel.Activity`.  
  
```  
<ic:Expression>  
  <wf:Operation Name="GetActivityType" />  
  <ic:Operation Name="Constant">  
    <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
  </ic:Operation>  
  <ic:Operation Name="Equals" />  
</ic:Expression>  
```