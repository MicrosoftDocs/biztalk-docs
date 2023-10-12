---
description: "Learn more about: Function 0x41: Set Event/Semaphore Handle"
title: "Function 0x41: Set Event-Semaphore Handle2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Function 0x41: Set Event/Semaphore Handle
This function supplies the driver with the handle of an event that can be used for signaling the SNALink software.  
  
## Parameters  
 **IRP.UserEvent**  
 This parameter is taken from the IOCTL call, and is an event handle. The handle must refer to an Event/Semaphore owned by the SNALink process. The driver sets the event to indicate the completion of a transmission or the availability of received data or status. Although not required by the driver, the event passed here by the SNALink is normally the global Base event.  
  
## Return Values  
 If the supplied parameter is NULL, the function returns a status of STATUS_INVALID_PARAMETER, with additional information of INFO_SET_EVENT_NO_EVENT. For any other illegal parameter, an exception is raised.  
  
## Remarks  
 This function should be called only once, immediately after the **OPEN** is issued. The event is set when:  
  
-   lFrames are transmitted from the driver buffers.  
  
-   lFrames are received into the driver buffers.  
  
-   lStatus information is updated in the Interface Record (see function 0x64).
