---
title: "IOCTL Command Summary2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9196e35f-bc2e-472a-b189-2e18bb743f3b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IOCTL Command Summary
The parameters to the IOCTL request packet are stored in the following fields in the associated I/O request packet (IRP).  
  
|IRP.CurrentStackLocation -> IOControlCode|Function code|  
|-------------------------------------------------|-------------------|  
|**IRP.SystemBuffer**|Address of parameter buffer (if used)|  
|**IRP.CurrentStackLocation -> InputBufferLength**|Length of parameter buffer|  
|**IRP.UserBuffer**|Address of data buffer|  
|**IRP.CurrentStackLocation -> OutputBufferLength**|Length of data buffer|  
  
 Note that under Windows, the operating system reserves the lower four bits of the IOCTL function codes to determine the method used to map the various buffers passed on the **DeviceIoControl** function call into the driver address space. The various options available to device driver writers are:  
  
|Low nibble|IOCTL definition|  
|----------------|----------------------|  
|0|METHOD_BUFFERED|  
|1|METHOD_IN_DIRECT|  
|2|METHOD_OUT_DIRECT|  
|3|METHOD_NEITHER|  
  
 For further details of the memory mapping performed by these various options, refer to the Windows documentation.  
  
 For a driver function code of ZZ, using memory mapping code M, the IOCTL code passed on the **DeviceIoControl** function call is 0xZZM.  
  
 The function codes are set out as shown in the table later in this topic. Note that all other function codes will be returned with the error ERROR_INVALID_DEVICE_REQUEST in the field **IoStatus.Status**. The Windows I/O System validates the address and length of the areas passed as parameter and data packets. If the address validation fails, an exception will be raised.  
  
 All requests must return immediately. In general, they are simple, immediate operations, but in the case of Transmit Frame and Receive Frame, the driver must not suspend the calling SNALink thread while waiting for I/O to complete—a relevant return code should be sent instead, allowing the SNALink to retry.  
  
 The complete list of functions is as follows.  
  
|Function|Function code|Windows IOCTL code|  
|--------------|-------------------|------------------------|  
|[Function 0x41: Set Event/Semaphore Handle](../core/function-0x41-set-event-semaphore-handle1.md)|0x41|0x410|  
|[Function 0x42: Set Link Characteristics](../core/function-0x42-set-link-characteristics2.md)|0x42|0x420|  
|[Function 0x43: Set V24 Output Status](../core/function-0x43-set-v24-output-status1.md)|0x43|0x430|  
|[Function 0x44: Transmit Frame](../core/function-0x44-transmit-frame2.md)|0x44|0x441|  
|[Function 0x45: Abort Transmitter](../core/function-0x45-abort-transmitter2.md)|0x45|0x450|  
|[Function 0x46: Abort Receiver](../core/function-0x46-abort-receiver2.md)|0x46|0x460|  
|[Function 0x47: Off-Board Load](../core/function-0x47-off-board-load2.md)|0x47|0x470|  
|[Function 0x61: Get/Set Interface Record](../core/function-0x61-get-set-interface-record1.md)|0x61|0x613|  
|[Function 0x62: Get V24 Status](../core/function-0x62-get-v24-status2.md)|0x62|0x622|  
|[Function 0x63: Receive Frame](../core/function-0x63-receive-frame1.md)|0x63|0x632|  
|[Function 0x64: Read Interface Record](../core/function-0x64-read-interface-record1.md)|0x64|0x642|  
  
 In the function descriptions in the following topics, the bit-numbering convention is: The bits in a byte are numbered 0 through 7, where bit 0 is the least significant and bit 7 is the most significant.  
  
> [!NOTE]
>  There is no function for the controlling autodialer across the synchronous dumb card interface. This autodial feature is implemented in the link service itself. The Microsoft link services that support the synchronous dumb card interface first perform the dial operation by sending the dial string containing the server-stored number to a COM port rather than the SDLC chip, and then sending a command to the device driver to raise DTR through a Set V24 Output Status IOCTL.