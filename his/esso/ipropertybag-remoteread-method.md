---
title: "IPropertyBag.RemoteRead Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9de1284-124b-4f0f-a8c9-c67cbc41153a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# IPropertyBag.RemoteRead Method
Writes the specified Single Sign-on (SSO) property.  
  
## Syntax  
  
```csharp  
  
void RemoteRead(  
string pszPropName,   
[out] object pVar,  
SSOAdminLib.IErrorLog pErrorLog,  
uint varType,  
object pUnkObj  
);  
  
```  
  
#### Parameters  
  
|Parameters|Description|  
|----------------|-----------------|  
|`pszPropName`|The property name to read.|  
|`pVar`|When returned, the object containing the property value.|  
|`pErrorLog`|An IErrorLog containing the error log, if applicable.|  
|`varType`|The object type of the property.|  
|`pUnkObj`|Pointer to the unknown object to read.|  
  
## Remarks  
 You can use IPropertyBag.Read to read the current settings for the SSO object model.  
  
## See Also  
 [IPropertyBag Methods1](../esso/ipropertybag-methods1.md)