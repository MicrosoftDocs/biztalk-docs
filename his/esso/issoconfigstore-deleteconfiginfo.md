---
title: "ISSOConfigStore::DeleteConfigInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3458abc-448b-4cee-8c7d-5f2ce8d8bca8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
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
 [ISSOConfigStore Interface (COM)](../esso/issoconfigstore-interface-com.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)