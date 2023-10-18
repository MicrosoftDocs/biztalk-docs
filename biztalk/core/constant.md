---
description: "Learn more about: Constant"
title: "Constant"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Constant
Pushes a single constant value onto the stack.  
  
## Syntax  
  
```  
  
<ic:Operation Name="Constant">  
  <ic:Argument>val</ic:Argument>  
</ic:Operation>  
```  
  
#### Parameters  
 Constant value.  
  
## Pushed Value  
 String containing the constant value.  
  
## Remarks  
  
## Example  
 The following sample filter expression uses the **Constant** operation to push a value that will then be used in an **Equals** operation to ensure that the current activity name is "FoodAndDrinksPolicy".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 This is a common usage pattern for the **Constant** operation.  
  
## See Also  
 [Interceptor Operations](../core/interceptor-operations.md)
