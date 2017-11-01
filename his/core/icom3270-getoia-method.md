---
title: "Icom3270.getOIA Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43229644-8680-4930-a3bb-67593c5db41b
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
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