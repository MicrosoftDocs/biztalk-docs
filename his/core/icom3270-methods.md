---
title: "Icom3270 Methods1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b28d466b-064d-4248-966f-433708c6011e
caps.latest.revision: 3
---
# Icom3270 Methods
The methods of the Icom3720 interfaces are listed in the following table. For a complete list of the IcomLU0 members, see [Icom3270 Members](../core/icom3270-members.md).  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[Icom3270.createSession Method](../core/icom3270-createsession-method.md)|Creates a new 3270 session.|  
|[Icom3270.getProperty Method](../core/icom3270-getproperty-method.md)|Describes the properties of a session.|  
|[Icom3270.connect Method](../core/icom3270-connect-method.md)|Connects a com3270 client to an existing session.|  
|[Icom3270.disconnect Method](../core/icom3270-disconnect-method.md)|Disconnects from a session.|  
|[Icom3270.setCursorPosition Method](../core/icom3270-setcursorposition-method.md)|Sets the position of the cursor on the 3270 screen.|  
|[Icom3270.getCursorPosition Method](../core/icom3270-getcursorposition-method.md)|Retrieves the current cursor position as an offset of the 3270 display buffer.|  
|[Icom3270.sendKey Method](../core/icom3270-sendkey-method.md)|Sends one or more keystrokes to the Host session.|  
|[Icom3270.wait Method](../core/icom3270-wait-method.md)|Waits for the session to enter a state where input is allowed or the screen is modified.|  
|[Icom3270.getOIA Method](../core/icom3270-getoia-method.md)|Returns a copy of the Operator Information Area (OIA) for the 3270 session.|  
|[Icom3270.getScreenSize Method](../core/icom3270-getscreensize-method.md)|Returns the size, in rows and columns, of the current 3270 screen.|  
|[Icom3270.getField Method](../core/icom3270-getfield-method.md)|Returns the starting position and length of the field containing the specified screen offset.|  
|[Icom3270.getNextField Method](../core/icom3270-getnextfield-method.md)|Finds the starting position and length of the field located after the specified offset.|  
|[Icom3270.getPrevField Method](../core/icom3270-getprevfield-method.md)|Finds the starting position and length of the field before the specified screen offset.|  
|[Icom3270.getFieldData Method](../core/icom3270-getfielddata-method.md)|Extracts the data contents of the specified field.|  
|[Icom3270.setFieldData Method](../core/icom3270-setfielddata-method.md)|Sets the data contents pf the specified field.|  
|[Icom3270.findFieldData Method](../core/icom3270-findfielddata-method.md)|Searches the specified field for the specified data string.|  
|[Icom3270.getScreenData Method](../core/icom3270-getscreendata-method.md)|Extracts the data contents of the 3270 screen.|  
|[Icom3270.setScreenData Method](../core/icom3270-setscreendata-method.md)|Copies data characters, character attributes, and extended attributers to all or part of the screen.|  
|[Icom3270.findScreenData Method](../core/icom3270-findscreendata-method.md)|Searches the screen for a specified data string.|