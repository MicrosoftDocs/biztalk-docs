---
title: "Batching Outgoing EDI Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93a2bd68-4974-4927-938a-8eaf8f007566
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batching Outgoing EDI Messages
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will batch EDI transaction sets if batching has been enabled for the agreement associated with the business partner that will be receiving it. The EDI properties for an agreement enable you to do the following:  
  
- Define multiple outgoing batches  
  
- Define the interchange  
  
- Define the groups in the interchange  
  
- Set the batch release criteria  
  
- Set the batch activation criteria.  
  
  Microsoft BizTalk Server EDI and AS2 enables the following processing of EDI interchanges:  
  
- EDI interchanges can include transaction sets and/or acknowledgments.  
  
- The EDI receive pipeline can split an interchange into XML transaction sets for further processing by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], or it can preserve the interchange, passing it through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in its received form.  
  
- The EDI routing orchestration enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to batch a single transaction set into more than one outgoing interchange.  
  
- The EDI batching orchestration assembles XML transaction sets into an EDI interchange, and validates and delivers the interchange according to an agreement's EDI properties.  
  
  EDI batches, called interchanges, contain message groups, and message groups contain individual messages. Outgoing batches can include multiple groups, but only one group per document type. A group can contain multiple transaction sets, but each must have the same document type. Message envelopes are used to wrap individual transaction sets, individual groups, and the entire interchange.  
  
## In This Section  
  
-   [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md)  
  
-   [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md)  
  
-   [Sending a Preserved Batch Interchange](../core/sending-a-preserved-batch-interchange.md)