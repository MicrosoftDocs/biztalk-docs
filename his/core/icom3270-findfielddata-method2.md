---
title: "Icom3270.findFieldData Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ce36f74-8860-466d-8f18-3f0d3621d00e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Icom3270.findFieldData Method
The findFieldData method searches the specified field for the specified data string.  
  
## Syntax  
  
```  
  
void FindFieldData(  
   ref ushort position,  
   ushort length,  
   ref System.Array dbuf  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`pos`|The 0-based screen offset of a character in the field to search.<br /><br /> When this method returns, contains the screen offset of the start of the data string, if the string was found.|  
|`length`|The length of the data to search on|  
|`dbuf`|Array containing the data to search on.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|C3270_S_TRUNCATED|The copy extended past the end of the field. The extra data was ignored.|  
|C3270_E_UNFORMATTED|The screen is formatted; therefore, the specified field does not exist.|  
|C3270_E_NOTFOUND|The specified data string could not be found.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 For the purpose of findFieldData, the field attribute character is considered part of the field. The field attribute character immediately precedes the field data.