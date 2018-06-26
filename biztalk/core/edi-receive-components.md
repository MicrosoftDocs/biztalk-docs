---
title: "EDI Receive Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d3b82e8-1168-4c2c-bf1a-886b43ff8108
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Receive Components
The pipeline and pipeline components described in this topic process EDI messages that are not EDI/AS2 messages. For information about the processing of received EDI/AS2 or non-EDI/AS2 messages, see [AS2 Receive Components](../core/as2-receive-components.md). Note that AS2 receive components perform EDI processing in addition to AS2 processing.  
  
## EDI Receive Pipeline  
 EDI receive processing is performed in the EDI Receive pipeline. This pipeline is installed in Microsoft.BizTalk.Edi.EdiPipelines.dll in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]. This pipeline processes EDI messages received over any transport. It does not process AS2-encoded EDI messages received over HTTP. Processing of AS2-encoded EDI messages is performed by the AS2 pipelines. The AS2 receive pipelines use the same components to process EDI messages as the EDI pipeline uses.  
  
> [!NOTE]
>  A security issue could occur if you create a receive location that uses the EDIReceive pipeline and has a transport type of HTTP. The EdiReceive pipeline will not generate an HTTP "200 OK" acknowledgment. If no EDI acknowledgment is returned, the connection will not be terminated gracefully, but will remain open. The connection will time out when the time-out period has expired.  
  
 The EDIReceive pipeline consists of the following pipeline components:  
  
-   EDI Disassembler  
  
-   BatchMarker.  
  
## EDI Receive Pipeline Components  
 The EDIReceive pipeline use the following pipeline components. These components are installed in Microsoft.BizTalk.Edi.PipelineComponents.dll in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components\\.  
  
### EDI Disassembler  
 The EDI Disassembler performs most processing of received EDI-encoded interchanges in the EDIReceive Pipeline. For information about how the EDI Disassembler processes EDI messages, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).  
  
### BatchMarker  
 The BatchMarker pipeline component prepares an interchange for batching by promoting the BatchId, ToBeBatched, and ToBeRouted context properties that are required for processing a batched interchange. How the BatchMarker component sets these properties depends upon how many trading partner agreements subscribes to the batch element.  
  
- If only one agreement subscribes to the batch element, the BatchMarker component sets the ToBeBatched context property to True, so that the batching orchestration picks up the batch element.  
  
- If more than one agreement subscribes to a batch element, the BatchMarker component sets the ToBeRouted context property to True, so that the routing orchestration picks up the batch element. It also sets the BatchIds context property to a space delimited list of batch IDs. The routing orchestration will then make one copy of the batch element for each batch ID, and set the ToBeBatched property to True on each copy of the batch element, so that the batching orchestration will pick up all copies.  
  
  The BatchMarker component is included in the last stage (trading partner agreement resolution) of the EDIReceive pipeline. All pipelines that will process EDI messages should include the BatchMarker pipeline component.  
  
> [!NOTE]
>  The BatchMarker component can be included in a receive pipeline that does not include the EDI Dissassembler, in order to perform trading partner agreement resolution without parsing the EDI message.  
  
 You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BatchMarker component to batch non-EDI messages. For more information, see the "Processing Non-EDI Messages in the BatchMarker Component" section of [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).  
  
## See Also  
 [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)