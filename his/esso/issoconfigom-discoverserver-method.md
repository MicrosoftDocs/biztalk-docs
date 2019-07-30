---
title: "ISSOConfigOM.DiscoverServer Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1161444-59f1-4b01-bb99-e40995cd9ea5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
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