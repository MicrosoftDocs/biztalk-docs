---
title: "Segment Delivery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a574761-0818-4452-b362-a8a30df8bc3a
caps.latest.revision: 3
---
# Segment Delivery
If the maximum request/response unit (RU) size for a session (supplied in the **BIND** parameters) allows RUs that are larger than the maximum size of a data link control transmission unit, for example, a Synchronous Data Link Control (SDLC) frame, the local node's path control is responsible for assembling outbound segments into RUs and segmenting inbound RUs where required.  
  
 However, certain IBM products (for example, SNA models of the 3270 controllers) do not perform outbound segment assembly, to improve perceived response times at display terminals by displaying each segment as soon as it is received. This feature is referred to as window shading.  
  
 The local node allows an application to specify a segment delivery option in the connection information control block (CICB) on the [Open(PLU) OK Response](../HIS2010/open-plu-oresponse1.md). If an application specifies this option, the local node's path control does not assemble outbound segments into complete RUs, and the local node delivers the segments to the application in [Data](../HIS2010/data2.md) messages. This enables an application emulating a 3270 device to reproduce the perceived response characteristics of the IBM device. In cases where throughput is high, such as 3270 file transfer, segment delivery can give improved performance compared to RU delivery.  
  
 Note that there is no comparable feature for inbound data. The application must present **Data** messages containing complete RUs to the local node. Also, there is no support for segment delivery on the system services control point (SSCP) session and connection (where the maximum RU size is limited to 256 bytes).  
  
 The local node supports the segment delivery option in such a way that the constraints placed on an application receiving data in either form are identical. If complete RUs are required, the local node rebuilds the RUs from segments in path control. If segments are required, the local node handles all segmentation indicators and modifies processing within its SNA layers to cater for segmented RUs.  
  
 All **Data** messages delivered to the application contain application flags, whereas only the first segment in an RU contains a response header (RH). The local node delays the end chain (EC) and change direction (CD) indicators if they occur in the RH of the RU's first segment, and sets the corresponding ECI and CDI application flags in the **Data** message corresponding to the last segment of the RU. Therefore, the **Data** messages corresponding to RU segments have application flags set as if they corresponded to whole RUs. This considerably simplifies the handling of chaining, bracket, and half-duplex protocols for an application using the segment delivery option.  
  
> [!NOTE]
>  EB is not delayed until end basic information unit (EBIU), because the application should use the [Status-Session](../HIS2010/status-session1.md) between-brackets message to determine when to enter the between-brackets state.  
  
## See Also  
 [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)   
 [PLU Session](../HIS2010/plu-session1.md)   
 [Outbound Chaining](../HIS2010/outbound-chaining1.md)   
 [Inbound Chaining](../HIS2010/inbound-chaining2.md)   
 [Brackets](../HIS2010/brackets2.md)   
 [Direction](../HIS2010/direction2.md)   
 [Pacing and Chunking](../HIS2010/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../HIS2010/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)   
 [Recovery](../HIS2010/recovery2.md)   
 [Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)   
 [LUSTATs\]](../HIS2010/lustats]2.md)   
 [Response Time Monitor Data](../HIS2010/response-time-monitor-data2.md)