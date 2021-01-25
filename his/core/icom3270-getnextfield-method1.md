---
description: "Learn more about: Icom3270.getNextField Method"
title: "Icom3270.getNextField Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab685ff6-b610-4b40-8f01-59bccbd28e95
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.getNextField Method
The getNextField method finds the starting position and length of the field located after the specified offset.  
  
## Syntax  
  
```  
  
void GetNextField(  
   ref ushort position,  
   ushort fieldType,  
   out ushort length  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|The 0-based screen offset from which to start the search.<br /><br /> When this method returns, contains the 0-based offset of the first data position of the following field.|  
|`fieldType`|The type of field requested. For more information, see the Remarks section.|  
|`length`|When this method returns, contains the length of the desired field, excluding the field attribute character.<br /><br /> Possible values are 0 through (screen size - 1).|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully.|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_UNFORMATTED|The screen is unformatted. Therefore, the specified field does not exist.|  
|C3270_E_NOTFOUND|The specified field could not be found.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icon3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 For the purpose of this search, the field attribute character is considered part of the field. The field attribute character immediately precedes the field data.  
  
 The following table describes the possible values for fieldType.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Either protected or unprotected.|  
|1|Unprotected field only.|  
|2|Protected field only.|
