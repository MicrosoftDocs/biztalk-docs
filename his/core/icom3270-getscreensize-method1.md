---
title: "Icom3270.getScreenSize Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e823323-2b5b-4525-b324-5e112ca2da51
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Icom3270.getScreenSize Method
The getScreenSize method returns the size, in rows and columns, of the current 3270 screen.  
  
## Syntax  
  
```  
  
void GetScreenSize(  
   out ushort rows,  
   out ushort cols  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`rows`|When this method returns, contains the number of rows on the current screen.|  
|`cols`|When this method returns, contains the number of columns on the current screen.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 You should call getScreenSize immediately after Icom3270.wait to determine whether the screen size has changed as a result of a Host application command.  
  
 You should not attempt to access or modify the screen buffers returned by the Icom3270.connect beyond the limits of the current screen size.