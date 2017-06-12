---
title: "GetActivityName | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 479552fa-1535-4f3d-90ff-4615f14c88b1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetActivityName
Pushes the name of the current activity onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetActivityName"/>  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current activity name.  
  
## Remarks  
 Windows Workflow Foundation performs its work as a series of activities configured by the developer. Each of these activities is assigned a unique name within the workflow. You can intercept data for a specific activity by filtering based on its unique name.  
  
## Example  
 The following sample contains an event filter expression configured to find a specific activity—FoodAndDrinksPolicy—in a Closed workflow. This is done by using a combination of operations including `GetActivityName`, `GetActivityEvent`, and logical operations.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 This filter pattern is common with Windows Workflow Foundation interceptor configuration files.  
  
> [!NOTE]
>  Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.