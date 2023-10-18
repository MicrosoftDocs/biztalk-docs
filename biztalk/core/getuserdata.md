---
description: "Learn more about: GetUserData"
title: "GetUserData"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# GetUserData
Pushes the current user data onto the stack.  
  
## Syntax  
  
```  
  
<wf:Operation Name="GetUserData" />  
```  
  
#### Parameters  
 None.  
  
## Pushed Value  
 String containing the current user data.  
  
## Remarks  
 This operation is not valid inside of a filter.  
  
## Example  
 The following sample contains an update expression for the data item "UserData" using the `GetUserData` operation.  
  
```  
<ic:Update DataItemName="UserData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetUserData" />  
  </ic:Expression>  
</ic:Update>  
```
