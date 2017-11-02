---
title: "Icom3270.getPrevField Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18827107-e4ce-4464-9658-f34e6245c899
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Icom3270.getPrevField Method
The getPrevField finds the starting position and length of the field before the specified screen offset.  
  
## Syntax  
  
```  
  
void GetPrevField(  
   ref ushort position,  
   ushort fieldType,  
   out ushort length  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|The 0-based screen offset to start searching from.<br /><br /> When this method returns, contains the 0-based offset of the first data position in the previous field.|  
|`fieldType`|The type of field requested. For more information, see the Remarks section.|  
|`length`|When this method returns, contains the length of the desired field, excluding the field attribute character.<br /><br /> Possible values are 0 through (screen size - 1).|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_UNFORMATTED|The screen is unformatted. Therefore, the specified field does not exist.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 For the purpose of getPrevField, the field attribute character is considered part of the field. The field attribute character immediately precedes the field.  
  
 The following table describes the possible values for `fieldType`.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Either protected or unprotected|  
|1|Unprotected field only|  
|2|Protected field only|