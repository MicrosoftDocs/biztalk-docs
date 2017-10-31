---
title: "Segment Delivery1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67c60193-6042-44a7-8b7d-a449f52f9ef5
caps.latest.revision: 3
---
# Segment Delivery
If the maximum request/response unit (RU) size for a session (supplied in the **BIND** parameters) allows RUs that are larger than the maximum size of a data link control transmission unit, for example, a Synchronous Data Link Control (SDLC) frame, the local node's path control is responsible for assembling outbound segments into RUs and segmenting inbound RUs where required.  
  
 However, certain IBM products (for example, SNA models of the 3270 controllers) do not perform outbound segment assembly, to improve perceived response times at display terminals by displaying each segment as soon as it is received. This feature is referred to as window shading.  
  
 The local node allows an application to specify a segment delivery option in the connection information control block (CICB) on the [Open(PLU) OK Response](../Topic/Open\(PLU\)%20OResponse1.md). If an application specifies this option, the local node's path control does not assemble outbound segments into complete RUs, and the local node delivers the segments to the application in [Data](../Topic/Data2.md) messages. This enables an application emulating a 3270 device to reproduce the perceived response characteristics of the IBM device. In cases where throughput is high, such as 3270 file transfer, segment delivery can give improved performance compared to RU delivery.  
  
 Note that there is no comparable feature for inbound data. The application must present **Data** messages containing complete RUs to the local node. Also, there is no support for segment delivery on the system services control point (SSCP) session and connection (where the maximum RU size is limited to 256 bytes).  
  
 The local node supports the segment delivery option in such a way that the constraints placed on an application receiving data in either form are identical. If complete RUs are required, the local node rebuilds the RUs from segments in path control. If segments are required, the local node handles all segmentation indicators and modifies processing within its SNA layers to cater for segmented RUs.  
  
 All **Data** messages delivered to the application contain application flags, whereas only the first segment in an RU contains a response header (RH). The local node delays the end chain (EC) and change direction (CD) indicators if they occur in the RH of the RU's first segment, and sets the corresponding ECI and CDI application flags in the **Data** message corresponding to the last segment of the RU. Therefore, the **Data** messages corresponding to RU segments have application flags set as if they corresponded to whole RUs. This considerably simplifies the handling of chaining, bracket, and half-duplex protocols for an application using the segment delivery option.  
  
> [!NOTE]
>  EB is not delayed until end basic information unit (EBIU), because the application should use the [Status-Session](../Topic/Status-Session1.md) between-brackets message to determine when to enter the between-brackets state.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection.md)   
 [PLU Session](../core/plu-session.md)   
 [Outbound Chaining](../core/outbound-chaining.md)   
 [Inbound Chaining](../core/inbound-chaining.md)   
 [Brackets](../core/brackets.md)   
 [Direction](../core/direction.md)   
 [Pacing and Chunking](../core/pacing-and-chunking.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data].md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce.md)   
 [Recovery](../core/recovery.md)   
 [Application-Initiated Termination](../core/application-initiated-termination.md)   
 [LUSTATs\]](../core/lustats].md)   
 [Response Time Monitor Data](../core/response-time-monitor-data.md)