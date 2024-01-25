---
description: "Learn more about: Equals"
title: "Equals"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Equals
Removes the top two items from the stack, compares the two items, and then pushes the result onto the stack.  
  
## Syntax  
  
```  
  
<ic:Operation Name="Equals" />  
```  
  
#### Parameters  
 Top two items on the stack.  
  
## Pushed Value  
 String result of the comparison operation.  
  
## Remarks  
  
## Example  
 The following example filter expression uses the **Equals** operation to compare the current activity name to the constant "CheckPO". If the two are equal, the expression evaluates to `true`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 You may be tempted to build your expression exactly as you would write a statement in C# when performing comparisons. For example, you might want to compare three values; in C# you would write something like:  
  
```  
bool res = a == b == c;  
```  
  
 However, as a model for your expression filter this falls a little short. Instead, consider the modified (but equivalent) statement:  
  
```  
Bool res = (a == b) && (a == c);  
```  
  
 This more closely matches the filter expression you would use to perform the comparison. For more details and an example, see [And](../core/and.md).  
  
## See Also  
 [Interceptor Operations](../core/interceptor-operations.md)
