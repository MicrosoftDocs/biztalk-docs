---
description: "Learn more about: IcomLUO.Disconnect Method"
title: "IcomLUO.Disconnect Method1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [IcomLU0 Methods](../core/icomlu0-methods1.md)   
 [Session Integrator for LU0](./session-integrator-for-lu02.md)
