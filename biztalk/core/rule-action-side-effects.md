---
description: "Learn more about: Rule Action Side Effects"
title: "Rule Action Side Effects"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Rule Action Side Effects
If the execution of an action affects the state of an object or a term used in conditions, that action is considered to have a side effect on the object.  
  
 Assume we have the following rules.  
  
## Rule 1  
  
```  
IF OrderForm.ItemCount > 100   
THEN OrderForm.Status = "important"  
```  
  
## Rule 2  
  
```  
IF OrderList.IsFromMember = true   
THEN OrderForm.UpdateStatus("important")  
```  
  
 In this case, **OrderForm.UpdateStatus** is said to have a side effect on **OrderForm.Status**. This does not mean that **OrderForm.UpdateStatus** has side effects; instead, **OrderForm.Status** is potentially affected by one or more actions.  
  
 By default, the **SideEffects** property for .NET class members is **true**, which prevents the rule engine from caching the member with side effects. In our example, the rule engine does not cache **OrderForm.Status** in the working memory; instead it gets the most up-to-date value of **OrderForm.Status** every time Rule 1 is evaluated. If the **SideEffects** property is set to **false**, the rule engine caches the value first time it evaluates **OrderForm.Status**, but for later evaluations (in forward-chaining scenarios), it uses the cached value.  
  
 Currently the Business Rule Composer does not provide a way for users to modify **SideEffects**, however, you can only set the **SideEffects** property programmatically through the Business Rules Framework. You set do this at binding, using the [ClassMemberBinding](/dotnet/api/microsoft.ruleengine.classmemberbinding) class to specify object methods, properties, and fields used in rule conditions and actions. **ClassMemberBinding** has a property, [SideEffects](/dotnet/api/microsoft.ruleengine.classmemberbinding.sideeffects), which contains a Boolean value indicating whether accessing the member changes its value.  
  
## See Also  
 [Rule Engine](../core/rule-engine.md)
