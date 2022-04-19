---
description: "Learn more about: Function 0x44: Transmit Frame"
title: "Function 0x44: Transmit Frame1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 409f1ad4-3ff6-46ca-8e3f-9fbede86fb4c
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Function 0x44: Transmit Frame
The SNALink calls this function to transfer a frame of data to the driver.  
  
## Parameters  
 **IRP.CurrentStackLocation.OutputBufferLength**  
 Frame length—the size of the frame pointed to by the data buffer pointer. The frame includes the control, address, and information field (if present), but no allowance should be made for flags or CRC bytes.  
  
 **IRP.UserBuffer**  
 Frame data—the contents of the frame.  
  
## Return Values  
  
|IoStatus.Status|IoStatus.Information|  
|---------------------|--------------------------|  
|STATUS_BUFFER_TOO_SMALL|IO_ERR_TX_BUFFER_FULL|  
|STATUS_INVALID_PARAMETER|IO_ERR_TX_FRAME_TOO_BIG|  
  
 Refer also to the description of the interface record—the driver updates a field within the interface record reflecting the amount of buffer space available.  
  
## Remarks  
 In two-wire configurations, the driver must raise RTS and wait for CTS from the modem before initiating a transmission. The driver should then drop RTS when all frames have been transmitted. The driver assumes that the transmission is complete when both of the following are true:  
  
-   The transmit buffer becomes empty (if the link is configured as half-duplex).  
  
-   The last frame transmitted had the Poll/Final bit set in the second byte.
