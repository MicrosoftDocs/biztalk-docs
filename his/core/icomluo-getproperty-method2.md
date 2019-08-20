---
title: "IcomLUO.GetProperty Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ec9e26f-a0c0-4ec5-8a36-6d6cbd91e5e7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# IcomLUO.GetProperty Method
Extracts both pre-defined and application-specific properties for the session.  
  
## Syntax  
  
```  
  
void SetProperty(  
   string PropertyName,  
   ref object value)  
  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`PropertyName`|The Name of the property to be extracted.|  
|`value`|When the method returns, contains the value of the specified property.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|CLU0_E_NOT_CONNECTED|The comLU0 client object is not connected to a session object through a call to Icom3270.Connect.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid. You should release the session handle.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for the specified comLU0 method, and has not yet returned.|  
|CLU0_E_BADPARAM|The specified property has not been defined for this session.|  
  
## Remarks  
 You can use getParameter, to determine the name of the pooled LU selected for the session when an LU0 session was originally created using an SNA Server pool name.  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods1.md)   
 [Session Integrator for LU0](./session-integrator-for-lu02.md)