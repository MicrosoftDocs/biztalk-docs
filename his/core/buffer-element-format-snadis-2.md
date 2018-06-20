---
title: "Buffer Element Format (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5368ec90-5429-4118-9c62-1d9d9ade2b0b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Buffer Element Format (SNADIS)
This topic lists the common fields that always occur at the start of a buffer element. The **dataru** field contains information specific to the particular message. For details about individual message formats, see [SNADIS Message Formats](./snadis-message-formats2.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|PTRBFELT|hdreptr–>elteptr|Pointer to next buffer element in the chain. NULL if this element is the last or only element in the chain.|  
|INTEGER|hdreptr–>startd|Start of valid data in this element. The index into *dataru* of the first byte of valid data.|  
|INTEGER|hdreptr–>endd|End of valid data in this element. The index into *dataru* of the last byte of valid data.|  
|CHAR|hdreptr–>trpad|Pad byte (reserved).|  
|CHAR[SNANBEDA]|hdreptr–>dataru|An array of characters that contains the data for this element. Note that the valid data might not occupy the whole of the element. The **startd** and **endd** fields give the indexes into this array of the start and end of the valid data. The constant SNANBEDA is defined in SNA_DLC.H as 268.|  
  
 The following information will help you to interpret the message formats:  
  
- Fields that occupy two bytes are represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. The exceptions to this are the **startd** and **endd** fields in elements, which are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).  
  
- The offsets indicated by the **startd** and **endd** fields are expressed in terms of the first byte of dataru being offset 1; the first byte of valid data is at **dataru(startd–1)**. For example, if **startd** is 11 and **endd** is 18, **dataru** begins with 10 bytes that are not valid data, followed by 8 bytes of valid data.  
  
  In the example message format illustrated in [Overview of Message Formats](../core/overview-of-message-formats-snadis-1.md), each element has a **startd** of 13, indicating 12 bytes of padding before the start of the valid data. This leaves room for 256 bytes of data, and hence the element data (300 bytes long in this example) requires two elements.