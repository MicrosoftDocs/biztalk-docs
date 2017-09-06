---
title: "GetWorkflowProperty | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9d3029e-3267-46bc-ba2e-1c6fa1f2e931
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetWorkflowProperty
Pushes the extracted property from the root activity of the workflow onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### Parameters  
 Name of the property.  
  
## Pushed Value  
 String containing the value of the property.  
  
## Remarks  
 This operation is only valid in Updates.  
  
 You can use dotted-notation for qualifying the property name you want to retrieve. This will provide you access to objects inside of other objects exposed through properties. For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".  
  
 Property names are case-sensitive first, and then case-insensitive. This is important when you have two or more activity properties that vary only by case in your WF application. For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match. If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-sensitive match after a case-insensitive match attempt fails.  
  
> [!NOTE]
>  NULL property values will result in a NullReferenceException being thrown back to the workflow instance.  
  
## Example  
 In the following sample, an update expression is used to persist the workflow property "City" from a purchase order by using `GetWorkflowProperty`.  
  
```  
<ic:Update DataItemName="City" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>po.Info.City</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```