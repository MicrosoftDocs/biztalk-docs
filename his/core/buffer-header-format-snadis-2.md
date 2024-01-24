---
description: "Learn more about: Buffer Header Format (SNADIS)"
title: "Buffer Header Format (SNADIS)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Buffer Header Format (SNADIS)
This topic lists the common fields that always occur at the start of a buffer header. These are followed by further fields specific to the particular message. For details about individual message formats, see [SNADIS Message Formats](./snadis-message-formats2.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|PTRBFHDR|nxtqptr|When the buffer is in a queue, this field points to the header of the next buffer in the queue (NULL if it is the last buffer in the queue). When the buffer is not in a queue, this field points to itself. The Host Integration Server buffer management routines use this to check for buffer corruption.|  
|PTRBFELT|hdreptr|Pointer to the first buffer element in the associated chain of buffer elements; NULL if the message consists only of a buffer header.|  
|CHAR|numelts|Number of buffer elements chained from the header. Zero if the message consists only of a buffer header.|  
|CHAR|msgtype|Message type. For more information, see individual message descriptions in [SNADIS Message Formats](./snadis-message-formats2.md).|  
|CHAR|srcl|Source locality. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
|CHAR|srcp|Source partner. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
|INTEGER|srci|Source index. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
|CHAR|destl|Destination locality. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
|CHAR|destp|Destination partner. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
|INTEGER|desti|Destination index. For more information, see [LPI Addresses](../core/lpi-addresses-snadis-2.md).|  
  
> [!NOTE]
>  Fields that occupy two bytes, such as **opresid** in the [Open(LINK)](./open-link-1.md) request, are normally represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. However, the following fields are exceptions:  
  
-   The **srci** and **desti** fields in buffer headers are stored in the local format of the application that assigns them (only the assigning application needs to interpret these values).  
  
-   The **startd** and **endd** fields in elements are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).
