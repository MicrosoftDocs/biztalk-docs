---
title: "GetUserData | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c243555b-109f-47e3-8084-ab13a8e22ac5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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