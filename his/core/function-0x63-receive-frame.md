---
title: "Function 0x63: Receive Frame2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53e6ef02-66fd-4939-a4ba-6c718e07a178
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Function 0x63: Receive Frame
The SNALink calls this function to read a data frame from the driver's buffers.  
  
## Parameters  
 **IRP.CurrentStackLocation.OutputBufferLength**  
 Frame length—the size of the frame transferred into the data buffer by the driver. The frame includes the control, address, and information field (if present), but no flags or CRC bytes. When the request is issued, frame length is set to the maximum length of the buffer addressed by the data packet pointer.  
  
 **IRP.UserBuffer**  
 Frame data—the contents of the frame that has been received.  
  
## Return Values  
  
|IoStatus.Status|IoStatus.Information|  
|---------------------|--------------------------|  
|STATUS_BUFFER_TOO_SMALL|None|  
  
## Remarks  
 The driver transfers the next available received frame to the supplied buffer. Note that if the buffer is not large enough, a buffer overflow error is returned. This allows the application to decide if oversize frames are an error. If not, then a second attempt to read should be made, using a buffer at least Frame Length bytes long. A length of zero is returned if there are no frames ready to be received.