---
title: "Buffer Header Format (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5f9fa06-027d-4e48-be65-2a5a92c34ad9
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Buffer Header Format (SNADIS)
This topic lists the common fields that always occur at the start of a buffer header. These are followed by further fields specific to the particular message. For details about individual message formats, see [SNADIS Message Formats](../Topic/SNADIS%20Message%20Formats1.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|PTRBFHDR|nxtqptr|When the buffer is in a queue, this field points to the header of the next buffer in the queue (NULL if it is the last buffer in the queue). When the buffer is not in a queue, this field points to itself. The [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] buffer management routines use this to check for buffer corruption.|  
|PTRBFELT|hdreptr|Pointer to the first buffer element in the associated chain of buffer elements; NULL if the message consists only of a buffer header.|  
|CHAR|numelts|Number of buffer elements chained from the header. Zero if the message consists only of a buffer header.|  
|CHAR|msgtype|Message type. For more information, see individual message descriptions in [SNADIS Message Formats](../Topic/SNADIS%20Message%20Formats1.md).|  
|CHAR|srcl|Source locality. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
|CHAR|srcp|Source partner. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
|INTEGER|srci|Source index. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
|CHAR|destl|Destination locality. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
|CHAR|destp|Destination partner. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
|INTEGER|desti|Destination index. For more information, see [LPI Addresses](../core/lpi-addresses-snadis.md).|  
  
> [!NOTE]
>  Fields that occupy two bytes, such as **opresid** in the [Open(LINK)](../Topic/Open\(LINK\)2.md) request, are normally represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. However, the following fields are exceptions:  
  
-   The **srci** and **desti** fields in buffer headers are stored in the local format of the application that assigns them (only the assigning application needs to interpret these values).  
  
-   The **startd** and **endd** fields in elements are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).