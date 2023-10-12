---
description: "Learn more about: Icom3270.getScreenData Method"
title: "Icom3270.getScreenData Method1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Icom3270.getScreenData Method
The getScreenData method extracts the data contents of the 3270 screen.  
  
## Syntax  
  
```  
  
void GetScreenData(  
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
|`position`|The 0-based screen offset of the first character requested.|  
|`dataRequested`|A bitwise combination describing the requested data. For more information, see the Remarks section.|  
|`maxLen`|The maximum number of .screen position requested.<br /><br /> Setting maxLen to 0 requests the remainder of the screen.|  
|`dbuf`|When this method returns, contains the screen data buffer data, if requested.|  
|`abuf`|When this method returns, contains the screen character attribute buffer data, if requested.|  
|`eabuf`|When this method returns, contains the screen extended attribute buffer data, if requested.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 You may request any combination of the displayable characters, character attributes, and extended attributes, of the screen.  
  
 Note that the returned data is contained in one or more SAFEARRAYS. You are responsible for releasing the SAFEARRAYS after processing.  
  
 The following table describes the possible values of dataRequested.  
  
|Value|Description|  
|-----------|-----------------|  
|1|Display buffer data|  
|2|Character attribute buffer data|  
|4|Extended attribute buffer data|
