---
description: "Learn more about: Concatenate"
title: "Concatenate"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Concatenate
Removes the top two items from the stack, concatenates them, and then pushes the result onto the stack.  
  
## Syntax  
  
```  
  
<ic:Operation Name="Concatenate" />  
```  
  
#### Parameters  
 Top two items on the stack.  
  
## Pushed Value  
 String result of the concatenation operation.  
  
## Remarks  
  
## Example  
 In the following example update expression, the constant string "Start:" is concatenated with the value of the "EventTime" context property and persisted to the database column NewOrderCreateTime.  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
## See Also  
 [Interceptor Operations](../core/interceptor-operations.md)
