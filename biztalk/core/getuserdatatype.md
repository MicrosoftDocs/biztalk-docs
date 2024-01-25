---
description: "Learn more about: GetUserDataType"
title: "GetUserDataType"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetUserDataType
Pushes the name of the current user data type onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetUserDataType" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current user data type in assembly-qualified format.  
  
## Remarks  
 Unlike **GetActivityType**, this operation does not use the assembly-qualified class name format; instead, it pushes only the type name:  
  
```  
MyLibrary.MyObject  
```  
  
> [!NOTE]
>  If you use the assembly-qualified class name format as a constant when comparing values it will always evaluate to `false`.  
  
## Special Filter Behavior  
 When this operation is performed inside of a filter, derived user data types are always matched as well.  
  
## Example  
 The following sample contains an event filter expression that will evaluate to `true` for `MyLibrary.MyObject` instances and for any instances from classes that derive from `MyLibrary.MyObject`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyLibrary.MyObject</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```
