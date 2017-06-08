---
title: "ISSOConfigStore::DeleteConfigInfo | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b6abd92-6108-4c16-a075-7306f9381f34
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOConfigStore::DeleteConfigInfo
The **DeleteConfigInfo** method deletes the configuration information from the config store.  
  
## Syntax  
  
```cpp#  
  
HRESULT DeleteConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
);  
```  
  
```vb  
  
DeleteConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
)  
```  
  
#### Parameters  
 `bstrApplication`  
 [in]  String containing the external application name.  
  
 `bstrApplication`  
 [in]  String containing the external application name.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This will typically be a GUID string.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This will typically be a GUID string.  
  
## Return Value  
 This method does not return a value.  
  
 The method returns an **HRESULT**. Possible values include, but are not limited to, those in the following table.  
  
|Return code|Description|  
|-----------------|-----------------|  
|S_OK|The config info was successfully returned from the config store.|  
|S_FALSE|The config info did not already exist.|  
|E_ACCESSDENIED|Access denied.|  
|E_INVALIDARG|Invalid argument.|  
  
## Remarks  
 If the config info specified by the parameters does not already exist in the config store, this method will return S_FALSE.  
  
 If the *bstrSSOServer* parameter is NULL, the Single Sign-On (SSO) server location is obtained from the registry. If the server location is not available in the registry, the local computer is used.  
  
## Example  
  
```  
  
ConfigStore  
bstrApplication  
bstrIdentifier  
  
```  
  
## See Also  
 [ISSOConfigStore Interface (COM)](../core/issoconfigstore-interface-com.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)