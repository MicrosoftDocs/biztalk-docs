---
title: "Chunking2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f3371b6-4cfb-477c-a2ee-638f13a8771d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Chunking
Chunking can be thought of as similar to segmentation. (For more information, see [Segment Delivery](../core/segment-delivery1.md).) The distinction is that segmentation is determined by the communications link between the local node and the remote system, whereas chunking is determined by the communications link between the application and the local node.  
  
 The application indicates on the [Open(SSCP) Request](./open-sscp-request2.md) whether it supports chunking, and, if so, the chunk size in bytes that it wants to use. The local node then uses the request/response unit (RU) size, the chunk size, and the segment size (if applicable) to determine whether chunking is necessary. It then specifies the chunk sizes used for inbound and outbound flow (which need not be the same) on the [Open(PLU) Request](./open-plu-request2.md). These values are specified in units of elements. (For more information, see [Messages](../core/messages2.md).) A value of zero for either of these sizes indicates that chunking is not necessary because the chunk size is not the limiting factor. Note that in chunking data, an RU will not be split in the middle of an element. This avoids data copying.  
  
 For example, assume that the local node is using an RU size of 8 kilobytes (KB) and segments of 2 KB, and the application's **Open(SSCP) Request** specifies segment delivery and a chunk size of 4 KB. Chunking will be used on inbound data flow (because the chunk size is smaller than the RU size), but is not necessary on outbound data flow (because data will be delivered in segments that are smaller than the chunk size).  
  
 If chunking is being used in either direction, all credit values specify the number of chunks that can be sent in that direction, not the number of RUs. Note that the segment delivery option is included on the **Open(SSCP) Request** to enable the local node to calculate the initial chunk credit values on the corresponding PLU connection. The application must also set this option on the **Open(PLU) Response**. If the **Open(SSCP) Request** and the **Open(PLU) Response** have different settings of this option, the setting from the **Open(PLU) Response** will be used. This can mean that the initial credit value used is not appropriate.  
  
 If session-level pacing is being used, the local node links this to the chunking credit. In particular, if the application withholds credit, the local node will delay sending a pacing response to the host, thereby applying back pressure to the host. This linkage is handled by the local node and need not concern the application.  
  
 Application flags on chunks of RUs are handled in the same way as those on segments. (For more information, see [Application Flags](../core/application-flags1.md) and [Segment Delivery](../core/segment-delivery1.md).) In particular:  
  
- FMHI, BCI, COMMIT, BBI, EBI, CODE, ENCRYP, ENPAD, QRI, and CEI are only set on the first chunk of an RU.  
  
- ECI and CDI are only set on the last chunk of an RU.  
  
- BBIUI is always set on the first chunk of an RU.  
  
- EBIUI is always set on the last chunk of an RU.  
  
  Note that EBI is set on the first chunk of the last RU in a bracket and not on the last chunk as might be expected. This is the same behavior as for segment delivery. The application should use the **Status-Session(BETB)** message, not the EBI flag, to determine when a bracket has ended.  
  
  Chunks are identified using the segmentation flags BBIUI and EBIUI, and therefore the application cannot distinguish between chunks and segments if both segmentation and chunking are being used outbound. However, there is generally no need for the distinction. The application can perform window shading by displaying each unit of data as it is received, whether the unit of data is a segment or a chunk. (For more information, see [Segment Delivery](../core/segment-delivery1.md).)  
  
> [!NOTE]
>  Previous versions of this document indicated this as a future feature. The support is enabled in Host Integration Server. Applications can test the product version returned on a call to [sepdgetinfo](./sepdgetinfo2.md) for version 1.2 or later before using the chunking system.  
  
 In some cases, the RU size used by the local node may be too large for the length of the path between the local node and an FMI application, for example, when using a 16 megabyte (MB) token-ring link, which can support 16 kilobyte (KB) frames. The local node allows an FMI application to specify that data transfer should be in smaller units, called chunks.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
 [PLU Session](../core/plu-session2.md)   
 [Outbound Chaining](../core/outbound-chaining2.md)   
 [Inbound Chaining](../core/inbound-chaining1.md)   
 [Segment Delivery](../core/segment-delivery1.md)   
 [Brackets](../core/brackets1.md)   
 [Direction](../core/direction1.md)   
 [Pacing and Chunking](../core/pacing-and-chunking1.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]1.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)   
 [Recovery](../core/recovery1.md)   
 [Application-Initiated Termination](../core/application-initiated-termination1.md)   
 [LUSTATs\]](../core/lustats]1.md)   
 [Response Time Monitor Data](../core/response-time-monitor-data1.md)