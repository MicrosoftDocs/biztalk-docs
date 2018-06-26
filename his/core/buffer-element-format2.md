---
title: "Buffer Element Format2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a54053b-20d4-4682-9853-448892fb0e7a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Buffer Element Format
The following table lists the common fields that always occur at the start of a buffer element. The **dataru** field contains information specific to the particular message. For details about individual message formats, see [FMI Message Formats](./fmi-message-formats2.md).  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|**hdreptr->elteptr**|PTRBFELT|Pointer to next buffer element in the chain. NULL if this element is the last or only element in the chain.|  
|**hdreptr->startd**|INTEGER|Start of valid data in this element. The index into **dataru** of the first byte of valid data.|  
|**hdreptr->endd**|INTEGER|End of valid data in this element. The index into **dataru** of the last byte of valid data.|  
|**hdreptr->trpad**|CHAR|Pad byte (reserved).|  
|**hdreptr->dataru**|CHAR[268]|An array of characters that contains the data for this element. Note that the valid data might not occupy the whole of the element. The **startd** and **endd** fields give the indexes into this array of the start and end of the valid data.|  
  
 Use the following information to help you interpret the message formats:  
  
- Certain messages are shown as having two elements in the message formats. For example, the [Open(PLU) Request](./open-plu-request2.md) has the **CICB** field in the first element and the **BIND RU** in the second element. This indicates that the message consists of two distinct linked element chains. The **elteptr** field in the first element points to the second element.  
  
- Fields that occupy two bytes are represented with the arithmetically most significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. The exceptions to this are the **startd** and **endd** fields in elements, which are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).  
  
- The offsets indicated by the **startd** and **endd** fields are expressed in terms of the first byte of **dataru** being offset 1. The first byte of valid data is at **dataru[startd–1]**. For example, if **startd** is 11 and **endd** is 18, **dataru** begins with 10 bytes that are not valid data, followed by 8 bytes of valid data.  
  
- It is possible for an element to arrive with **startd** greater than **endd**. This indicates there is no valid data in **dataru**.  
  
  In the sample message format shown in [Overview of Message Formats](../core/overview-of-message-formats1.md), each element has a **startd** of 13, indicating 12 bytes of padding before the start of the valid data. This leaves room for 256 bytes of data, and so the element data (300 bytes long in this example) requires two elements.