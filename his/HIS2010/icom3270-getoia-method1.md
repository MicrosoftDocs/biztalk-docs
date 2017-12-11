---
title: "Icom3270.getOIA Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cac67f11-a95f-4a00-be81-3c3f8eb17bdc
caps.latest.revision: 4
---
# Icom3270.getOIA Method
The getOIA method returns a copy of the Operator Information Area (OIA) for the 3270 session.  
  
## Syntax  
  
```  
  
void GetOIA(  
   out System.Array oiaBuffer  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`oiaBuffer`|When this method returns, contains the buffer into which the current OIA is copied. For more information, see the Remarks section.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|C3270_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 The OIA is a bit map that provides information regarding the status of the current screen. You may use the OIA to determine the ownership of the session, and the reason for input-inhibited errors.  
  
 As defined by COM, it is your responsibility to release the memory of the returned SAFEARRAY structures.