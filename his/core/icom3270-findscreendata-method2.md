---
title: "Icom3270.findScreenData Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc5a7ac-09cd-40cf-88ff-79f1a2f38bbe
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.findScreenData Method
The findScreenData method searches the screen for a specified data string.  
  
## Syntax  
  
```  
  
void FindScreenData(  
   ref ushort position,  
   ushort length,  
   ref System.Array dbuf  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|on input, the 0-based screen offset describing the location on which to begin the search.<br /><br /> On a successful return, contains the screen offset of the start of the data string.|  
|`length`|The length of the array containing the data to search on.|  
|`dbuf`|An array containing the data to search on.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_NOTFOUND|The specified data string could not be found.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks