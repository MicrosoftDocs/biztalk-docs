---
title: "Icom3270.getFieldData Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e98f3b6e-de8f-40c5-b8e7-2a7803773501
caps.latest.revision: 4
---
# Icom3270.getFieldData Method
Extracts the data contents of the specified field.  
  
## Syntax  
  
```  
  
void GetFieldData(  
   ushort position,  
   ushort dataRequested,  
   ushort maxLen,  
   out System.Array dbuf,  
   out System.Array abuf,  
   out System.Array eabuf  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|The 0-based screen offset of a character in the specified field.|  
|`dataRequested`|A bitwise combination describing the data requested. For more information, see the Remarks section.|  
|`maxLen`|The maximum number of .screen positions requested.<br /><br /> 0 indicates a request for the entire field.|  
|`dbuf`|When this method returns, contains the screen data buffer data, if necessary.|  
|`abuf`|When this method returns, contains the screen character attribute buffer data, if necessary.|  
|`eabuff`|When this method returns, contains the screen extended attribute buffer data, if necessary.|  
  
## Property Value/Return Value  
  
## Exceptions  
  
## Remarks  
 getFieldData does not extract the Field Attribute character.  
  
 You may request any combination of the displayable characters, character attributes, and extended attributes of the field.  
  
 You are responsible for releasing the SAFEARRAYs that the method returns the specified data in.  
  
 For the purpose of getFieldData the field attribute character, which immediately precedes the field data, is considered part of the field.  
  
 The following table describes the possible values for `dataRequested`.  
  
|Value|Description|  
|-----------|-----------------|  
|1|Display buffer data|  
|2|Character attribute buffer data|  
|4|Extended attribute buffer data|