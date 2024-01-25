---
description: "Learn more about: GetUserKey"
title: "GetUserKey"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetUserKey
Pushes the current user key onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetUserKey" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current user key.  
  
## Remarks  
 This operation is valid only in user track points.  
  
## Example  
 The following sample contains an event filter expression that will evaluate to `true` when the user key is equal to "DocumentUrl".  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```
