---
title: "GetActivityProperty | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2321f1ec-d98d-478f-bb1d-a11a98e60fa5
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# GetActivityProperty
Pushes the extracted property from the activity related to the tracking event onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetActivityProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### Parameters  
 Name of the property.  
  
## Return Value  
 String containing the value of the property.  
  
## Remarks  
 You can use dotted-notation for qualifying the property name you want to retrieve. This will provide you access to objects inside of other objects exposed through properties. For example, to access the City property of an Address instance of a purchase order, use "purchaseOrder.Address.City".  
  
 Property names are case-sensitive first, and then case-insensitive. This is important when you have two or more activity properties that vary only by case in your WF application. For example, if your workflow application has the properties "myWorkflow" and "MyWorkflow" defined and you were looking for "MyWorkflow", it would match on the second property through a case-sensitive match. If you specify "MYWORKFLOW", it would match "myWorkflow" through a case-insensitive match after a case-sensitive match attempt fails.  
  
 For example, if you have two activity properties that vary only by case: "myProperty" and "MyProperty".  
  
> [!NOTE]
>  NULL property values will result in a NullReferenceException being thrown back to the workflow instance.  
  
## Example  
 In the following sample, an update expression is used to persist the activity property "MyProperty" by using `GetActivityProperty`.  
  
```  
<ic:Update DataItemName="TextData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetActivityProperty">  
      <wf:Argument>MyProperty</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```