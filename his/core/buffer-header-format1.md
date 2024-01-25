---
description: "Learn more about: Buffer Header Format"
title: "Buffer Header Format1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Buffer Header Format
The following table lists the common fields that always occur at the start of a buffer header. These are followed by further fields specific to the particular message. For details about individual message formats, see [FMI Message Formats](./fmi-message-formats2.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|**nxtqptr**|PTRBFHDR|When the buffer is in a queue, this field points to the header of the next buffer in the queue (NULL if it is the last buffer in the queue). When the buffer is not in a queue, this field points to itself. The SNA server buffer management routines use this field to check for buffer corruption.|  
|**hdreptr**|PTRBFELT|Pointer to the first buffer element in the associated chain of buffer elements. NULL if the message consists only of a buffer header.|  
|**numelts**|CHAR|Number of buffer elements chained from the header. Zero if the message consists only of a buffer header.|  
|**msgtype**|CHAR|Message type. For details, see individual message descriptions in [FMI Message Formats](./fmi-message-formats2.md).|  
|**srcl**|CHAR|Source locality. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
|**srcp**|CHAR|Source partner. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
|**srci**|INTEGER|Source index. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
|**destl**|CHAR|Destination locality. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
|**destp**|CHAR|Destination partner. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
|**desti**|INTEGER|Destination index. For details, see [LPI Addresses](../core/lpi-addresses1.md).|  
  
> [!NOTE]
>  Fields that occupy two bytes, such as **opresid** in [Open(PLU) Request](./open-plu-request2.md) are normally represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. However, the following fields are exceptions:  
  
-   The **srci** and **desti** fields in buffer headers are stored in the local format of the application that assigns them (only the assigning application needs to interpret these values).  
  
-   The **startd** and **endd** fields in elements are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).
