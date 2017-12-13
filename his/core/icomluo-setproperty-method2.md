---
title: "IcomLUO.SetProperty Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93731964-e68f-4da9-8b5c-54072aa9bc5e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IcomLUO.SetProperty Method
Allows the comLU0 client to set property values for a session.  
  
## Syntax  
  
```  
  
void SetProperty(  
   string PropertyName,  
    ref object value)  
  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`PropertyName`|The name of the property to be added or updated.|  
|`Value`|The value of the specified property.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The requested property was added successfully.|  
|CLU0_S_PROP_UPDATED|The existing property specified was updated successfully|  
|CLU0_E_NOT_CONNECTED|The comLU0 client object is not connected to a session object through a call to the IcomLU0.Connect method.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid. You should release the session handle.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for the specified comLU0 method which has not yet returned.|  
|CLU0_E_BADPARAM|The specified property is a pre-defined session property, and therefore could not be updated.|  
  
## Remarks  
 Property names are case-insensitive.  
  
 You cannot use SetProperty to modify any of the predefined connection properties. Instead, you can change only the properties defined with CreateSession.  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods1.md)   
 [Session Integrator for LU0](../HIS2010/session-integrator-for-lu01.md)