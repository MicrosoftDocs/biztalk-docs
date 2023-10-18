---
description: "Learn more about: ISSOConfigOM.DiscoverServer Method"
title: "ISSOConfigOM.DiscoverServer Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
