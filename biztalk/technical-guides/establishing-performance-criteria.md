---
title: "Establishing Performance Criteria | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 181011d1-aa74-43fe-b05a-30b043956d70
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Establishing Performance Criteria
The performance goals of a BizTalk Server solution typically fall into one of two categories, throughput or latency. This topic describes the factors that should be considered when evaluating the throughput or latency of a BizTalk Server solution.  
  
> [!NOTE]  
>  Optimizing throughput or latency of a BizTalk Server solution often represents conflicting goals. For example, you might improve the throughput of the file receive adapter by increasing the batch size, but doing so would reduce latency. In this scenario the adapter takes longer to accumulate messages for a larger batch size, which in turn will reduce end-to-end latency for a given message.  
  
## Factors affecting throughput of a BizTalk Server solution  
 **Throughput**- Broadly measured as the number of documents that a BizTalk Server solution can process within a given time interval.  
  
 Factors that affect throughput include:  
  
-   **Message size** – Larger messages consume more overhead than smaller messages, especially if the messages are transformed with a map and are large enough so that they are buffered to the file system during the mapping operation. For more information about how message size affects BizTalk Server performance, see [How BizTalk Server Processes Large Messages](http://go.microsoft.com/fwlink/?LinkId=139293) (http://go.microsoft.com/fwlink/?LinkId=139293).  
  
-   **Message format** - Messages are received into BizTalk Server in one of two primary formats, XML files or flat files. Because flat files must be translated into the XML format to be processed by the BizTalk Messaging engine, additional overhead is incurred by the processing of flat files.  
  
-   **Adapter requirements** – Different adapters frequently have varying performance capabilities. For example, adapters that require MSDTC transaction support will incur additional overhead/reduced performance as compared to an adapter that does not use MSDTC transactions. Adapters used by the BizTalk solution will vary depending on your trading partner’s requirements and/or internal business needs.  
  
-   **Orchestration processing requirements** – Orchestrations provide great flexibility for encapsulating and applying business processes to messages received by BizTalk. At the same time, orchestrations consume overhead, which must be considered when estimating the throughput of a BizTalk Server solution.  
  
-   **Peak load requirements** – Most document processing does not necessarily occur in a measured orderly fashion. For example, a BizTalk Server solution may sustain a large percentage of its processing load at the close of a business day. Therefore peak load requirements and the Maximum Sustainable Throughput (MST) of a BizTalk Server solution should be taken into account when establishing throughput criteria. For more information about measuring the MST of a BizTalk Server solution, see [Measuring Maximum Sustainable Engine Throughput](http://go.microsoft.com/fwlink/?LinkID=154388) (http://go.microsoft.com/fwlink/?LinkID=154388) and [Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815).  
  
-   **Document tracking requirements** – Document tracking imposes additional overhead on the system. Document tracking requirements should be a primary consideration when estimating the throughput goals of a BizTalk solution.  
  
## See Also  
 [BizTalk Server Performance Testing Methodology](../technical-guides/biztalk-server-performance-testing-methodology.md)