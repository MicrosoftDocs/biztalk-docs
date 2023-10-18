---
description: "Learn more about: Icom3270.disconnect Method"
title: "Icom3270.disconnect Method1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Icom3270.disconnect Method
The disconnect method disconnects from a session.  
  
## Syntax  
  
```  
  
void Disconnect()  
```  
  
#### Parameters  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 After you call disconnect, even if the call fails, you must call Icom3270.connect again before accessing the session.
