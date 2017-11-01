---
title: "IcomLUO.Disconnect Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 573e60fd-7380-4326-9064-7a84636e53be
caps.latest.revision: 4
---
# IcomLUO.Disconnect Method
Disconnects from a previously-connected session.  
  
## Syntax  
  
```  
  
void Disconnect()  
```  
  
#### Parameters  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|CLU0_E_NOTCONNECTED|The comLU0 client is not connected to a session through a call to IcomLU0.Connect.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> You should release the session handle.|  
|CLU_E_WAITING|Another thread has issued a receive call for this comLU0 method, and has not yet returned.|  
|CLU0_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 After your call to Disconnect is complete, you must call Connect again in order to access the session. This is true regardless of whether your call to Disconnect was successful.  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods.md)   
 [Session Integrator for LU0](../Topic/Session%20Integrator%20for%20LU01.md)