---
title: "Icom3270.getField Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64b020b6-8cc7-4bc1-9bb6-725524dff048
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.getField Method
The getField method returns the starting position and length of the field containing the specified screen offset.  
  
## Syntax  
  
```  
  
void GetField(  
   ref ushort position,  
   out ushort length  
 )  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|The 0-based screen offset of a character in the desired field.<br /><br /> Note that the calculation used by getField considers the field attribute character part of the field. The field attribute character immediately precedes the field data.<br /><br /> When this method returns, contains the 0-based offset of the first data position of the field.|  
|`length`|When this method returns, contains the length of the desired field, excluding the field attribute character.<br /><br /> Possible values range between 0 and (screen size - 1).|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|C3270_E_INVALIDPOS|The screen position specified is greater than the maximum character position for the current screen size.|  
|C3270_E_UNFORMATTED|The screen is unformatted. Therefore, the specified field does not exist.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session object through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks