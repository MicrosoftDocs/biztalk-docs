---
description: "Learn more about: FMI Message Formats"
title: "FMI Message Formats2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FMI Message Formats
This section describes the message formats for the function management interface (FMI). The message formats are presented in a language-independent notation. Details of the message format notation and key assumptions about the contents of the message formats are as follows:  
  
-   Reserved indicates that the field is set to zero (for a numeric field) or all nulls (for names) by the sender of the message.  
  
-   Undefined indicates that the value of the field is indeterminate. The field is not set by the sender and should not be examined by the receiver of the message.  
  
-   Fields that occupy two bytes, such as **opresid** in the [Open(PLU) Request](../core/open-plu-request2.md), are represented with the most arithmetically significant byte in the lowest byte address, irrespective of the normal orientation used by the processor on which the software executes. That is, the 2-byte value 0x1234 has the byte 0x12 in the lowest byte address. However, the following fields are exceptions:  
  
    -   The **srci** and **desti** fields in buffer headers are stored in the local format of the application that assigns them, because only the assigning application needs to interpret these values.  
  
    -   The **startd** and **endd** fields in elements are always stored in low-byte, high-byte orientation (the normal orientation of an Intel processor).  
  
-   Messages are composed of buffers consisting of a buffer header and zero or more buffer elements. For more information about buffer formats, see [Messages](./messages2.md).  
  
-   Applications must assign unique index (I) values for every active LPI connection within the node. In particular, the [Open(SSCP) Request](../core/open-sscp-request2.md) must be different from the source index it sends in response to the [Open(PLU)](../core/open-plu-1.md). Additionally, zero should not be used as an I value. An I value of zero means that the sender of the message is inviting the recipient of the message to assign an I value.  
  
-   The **startd** field in each element gives the offset of the first byte of data in the element after the **trpad** field.  
  
     For non-logical unit application (LUA) applications, **startd** will either be 1 (data starts in the byte after the **trpad** field), 10 (nine bytes of padding are included between the **trpad** field and the start of the data), or 13 (12 bytes of padding are included between the **trpad** field and the start of the data).  
  
     For LUA applications, **startd** is 4 (three bytes of padding between the **trpad** field and the start of the data) in the first element of a message and 13 (12 bytes of padding) in subsequent elements.  
  
     The local node uses extra bytes for additional header information. This avoids having to copy data into a new buffer when adding this information.  
  
-   Because **startd** indicates the index into **dataru** starting from 1, not 0, the first byte of valid data is always at **dataru[startd–1]**.  
  
-   If **startd** is greater than **endd**, there is no valid data in the message.  
  
-   All fields within **dataru** are of type **CHAR**, except where the remarks indicate otherwise.  
  
-   Note that where a buffer element has a **startd** of 1, 10, or 13, this only applies to the initial element in the chain of elements, and subsequent elements in the chain have a **startd** of 1. Messages with two distinct linked element chains in the message formats (for example [Open(PLU) Request](../core/open-plu-request2.md) and [Open(PLU) OK Response](../core/open-plu-oresponse2.md)) have the **startd** field in the elements at the start of the chains as the value (1, 10, or 13) given in the message format, and the **startd** fields in all other elements as 1.  
  
## In This Section  
  
-   [Open(SSCP)](../core/open-sscp-2.md)  
  
-   [Open(SSCP) Request](../core/open-sscp-request2.md)  
  
-   [Open(SSCP) Response](../core/open-sscp-response1.md)  
  
-   [Open(PLU)](../core/open-plu-1.md)  
  
-   [Open(PLU) Request](../core/open-plu-request2.md)  
  
-   [Open(PLU) OK Response](../core/open-plu-oresponse2.md)  
  
-   [Open(PLU) Error Response](../core/open-plu-error-response2.md)  
  
-   [Open(PLU) OK Confirm](../core/open-plu-oconfirm1.md)  
  
-   [Open(PLU) Error Confirm](../core/open-plu-error-confirm2.md)  
  
-   [Close(SSCP)](../core/close-sscp-2.md)  
  
-   [Close(SSCP) Request](../core/close-sscp-request2.md)  
  
-   [Close(SSCP) Response](../core/close-sscp-response1.md)  
  
-   [Close(PLU)](../core/close-plu-2.md)  
  
-   [Close(PLU) Request](../core/close-plu-request2.md)  
  
-   [Close(PLU) Response](../core/close-plu-response2.md)  
  
-   [Data](../core/data1.md)  
  
-   [Status-Acknowledge](../core/status-acknowledge1.md)  
  
-   [Status-Acknowledge(Ack)](../core/status-acknowledge-ack-2.md)  
  
-   [Status-Acknowledge(Nack-1)](../core/status-acknowledge-nack-1-1.md)  
  
-   [Status-Acknowledge(Nack-2)](../core/status-acknowledge-nack-2-2.md)  
  
-   [Status-Acknowledge(ACKLUA)](../core/status-acknowledge-acklua-2.md)  
  
-   [Status-Control](../core/status-control1.md)  
  
-   [Status-Control(...) Request](../core/status-control-request2.md)  
  
-   [Status-Control(...) Acknowledge](../core/status-control-acknowledge1.md)  
  
-   [Status-Control(...) Negative-Acknowledge-1](../core/status-control-negative-acknowledge-11.md)  
  
-   [Status-Control(...) Negative-Acknowledge-2](../core/status-control-negative-acknowledge-21.md)  
  
-   [Status-Control(...) ACKLUA](../core/status-control-acklua1.md)  
  
-   [Status-Error](../core/status-error1.md)  
  
-   [Status-Resource](../core/status-resource1.md)  
  
-   [Status-RTM](../core/status-rtm1.md)  
  
-   [Status-Session](../core/status-session2.md)
