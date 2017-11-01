---
title: "Function 0x42: Set Link Characteristics1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df9497a1-67ee-440e-a656-de9bf363d645
caps.latest.revision: 3
---
# Function 0x42: Set Link Characteristics
This function sets the link protocol parameters required by the driver.  
  
## Packet Formats  
  
|Type|Description|  
|----------|-----------------|  
|WORD|Frame Size|  
|DWORD|Data rate|  
|BYTE|Station address 1|  
|BYTE|Station address 2|  
|BYTE|Link Options|  
|BYTE|Reserved|  
  
## Parameters  
 *Frame Size*(packet format WORD)  
 Indicates to the driver the minimum amount of contiguous receiver buffering that must be available for any individual frame.  
  
 *Data Rate*(packet format DWORD)  
 Line speed in bits per second. If *Link Options* bit 3 is not set, this field is ignored.  
  
 *Station Address 1*(packet format BYTE)  
  *Station Address 2*(packet format BYTE)  
 Station addresses that the user wishes to receive on if selective reception is to be used (typically for multidropped secondaries). Only frames of data beginning with either of these values will be passed to the user—others are ignored or discarded.  
  
 If the SNALink wishes to listen on only one station address, *Station Address 2* should be set to zero.  
  
 A value of zero in both fields indicates that all error-free received frames are to be passed to the SNALink, regardless of the contents of their first address byte.  
  
 *Link Options*(packet format BYTE)  
 *Link Options* is a bitmap. The default is all values set to zero. The bits are used as shown in the following table. Note that not all of these options are supported by the standard Microsoft [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] synchronous card drivers.  
  
|Bit|Value|  
|---------|-----------|  
|Bit 7|1 = Four wire (constant RTS/CTS). 0 = Two wire (switched RTS/CTS).|  
|Bit 6|1 = NRZI encoding. 0 = NRZ encoding.|  
|Bit 5|1 = HDLC level 1 conventions. 0 = SDLC level 1 conventions.|  
|Bit 4|1 = Full-duplex (simultaneous 2-way) data. 0 = Half-duplex (alternating 1-way) data.|  
|Bit 3|1 = Generate internal clocking.  0 = Take external clocking.|  
|Bit 2|1 = Use DMA if available. 0 = Do not use DMA on this link.|  
|Bit 1|1 = Reset all statistics to zero. 0 = Leave accumulated statistics as is.|  
|Bit 0|Reserved.|  
  
 *Reserved*(packet format BYTE).  
 Reserved.  
  
> [!NOTE]
>  Not all of the above options are supported by the standard Host Integration Server synchronous card drivers.  
  
## Return Values  
  
|IoStatus.Status|IoStatus.Information|Description|  
|---------------------|--------------------------|-----------------|  
|STATUS_INVALID_PARAMETER|IO_ERR_LINKCHARBUF_ WRONG_SIZE||  
|STATUS_INVALID_PARAMETER|IO_ERR_FRAME_BUF_ TOO_SMALL|Buffer must be at least 268 bytes.|  
|STATUS_INVALID_PARAMETER|IO_ERR_FRAME_BUF_ TOO_BIG|Buffer maximum size is 2048 bytes.|  
|STATUS_INVALID_PARAMETER|IO_ERR_NO_CLOCKS|No internal clocking available.|  
|STATUS_DATA_ERROR|IO_ERR_HARDWARE_ 8273CMD_TIMEOUT||  
|STATUS_SUCCESS|IO_ERR_NO_DMA_FDX|DMA requested, but cannot be used.|  
  
## Remarks  
 The driver should always start the receiver after processing this request. If either the transmitter or receiver is active when this request is issued, the driver stops the current frame before resetting the link characteristics, and then restarts the previous operation.  
  
 Link Service DLLs that support the synchronous dumb card interface use the following registry entries to the control this feature.  
  
 **SYSTEM\CurrentControlSet\Services\\<linkService\>\Parameters**  
  
 where **\<linkService>** is the name of the link service.  
  
 Under this node, the following entries and values must be entered or modified:  
  
 A node called **ExtraParameters** must be created or modified with the following registry entries and values:  
  
 **InternalClock**  
 The value of this entry should be defined and set to a REG_DWORD of any value to enable the internal clock.  
  
 **InternalClockRate**  
 The value of this entry should be set to a REG_DWORD equal to the number of bits per second.