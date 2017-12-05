---
title: "Buffer Header Format2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6bf934e-5cc2-4a97-9c98-0c2581861f74
caps.latest.revision: 3
---
# Buffer Header Format
The following table lists the common fields that always occur at the start of a buffer header. These are followed by further fields specific to the particular message. For details about individual message formats, see [FMI Message Formats](../core/fmi-message-formats1.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|**nxtqptr**|PTRBFHDR|When the buffer is in a queue, this field points to the header of the next buffer in the queue (NULL if it is the last buffer in the queue). When the buffer is not in a queue, this field points to itself. The SNA server buffer management routines use this field to check for buffer corruption.|  
|**hdreptr**|PTRBFELT|Pointer to the first buffer element in the associated chain of buffer elements. NULL if the message consists only of a buffer header.|  
|**numelts**|CHAR|Number of buffer elements chained from the header. Zero if the message consists only of a buffer header.|  
|**msgtype**|CHAR|Message type. For details, see individual message descriptions in [FMI Message Formats](../core/fmi-message-formats1.md).|  
|**srcl**|CHAR|Source locality. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
|**srcp**|CHAR|Source partner. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
|**srci**|INTEGER|Source index. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
|**destl**|CHAR|Destination locality. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
|**destp**|CHAR|Destination partner. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
|**desti**|INTEGER|Destination index. For details, see [LPI Addresses](../core/lpi-addresses2.md).|  
  
> [!NOTE]
>  Fields that occupy two bytes, such as **opresid** in [Open(PLU) Request](../core/open-plu-request1.md) are normally represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. However, the following fields are exceptions:  
  
-   The **srci** and **desti** fields in buffer headers are stored in the local format of the application that assigns them (only the assigning application needs to interpret these values).  
  
-   The **startd** and **endd** fields in elements are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).