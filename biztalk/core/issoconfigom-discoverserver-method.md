---
title: "ISSOConfigOM.DiscoverServer Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 076f04db-1bdf-4e0a-83c2-fc224141a630
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOConfigOM.DiscoverServer Method
The **DiscoverServers** method discovers the currently-available servers.  
  
## Syntax  
  
```vb  
  
Servers As String  
);  
```  
  
```csharp  
  
BSTR Servers   
);  
```  
  
#### Parameters  
  
|Parameter|Reference|  
|---------------|---------------|  
|`Servers`|Returns a string containing the currently-available servers.|  
  
## Exceptions  
 [C++] This method returns an HRESULT containing one of the values in the following table.  
  
 [Visual Basic] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDREG|An invalid parameter was detected.|