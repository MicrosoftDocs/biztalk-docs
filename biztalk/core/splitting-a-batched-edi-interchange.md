---
title: "Splitting a Batched EDI Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c79b06-cc88-4cc8-aa99-40f24a1bdcde
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Splitting a Batched EDI Interchange
> [!NOTE]
>  All the user interface options mentioned in this topic are available in the **Local Host Settings** page (**Receiver’s Settings** section) of the one-way agreement tabs in the **Agreement Properties** dialog box.  
  
 The EDI receive pipeline splits an incoming EDI interchange batch if you have set the **Inbound batch processing option** agreement property to **Split Interchange as Transaction Sets**.  
  
 When the EDI receive pipeline splits an incoming batched EDI interchange, it creates one XML file for each EDI transaction set/message. The pipeline promotes the entire interchange and group headers into the context of each transaction set split from the interchange. It also promotes certain specific interchange and group headers, such as ISA6, GS1, and GS2, so that these fields can be used for routing. You can mask the security information in the header by selecting the **Mask security/authorization/password information** property.  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attempts to split an interchange into transaction sets, any error in certain ISA (ISA1 through ISA13) or UNB header fields will lead to the interchange being rejected. This is also the case when the interchange control number is a duplicate, if the check for a duplicate interchange control number is enabled in the agreement or fallback agreement properties. An error in other interchange header fields (other than ISA1 through ISA13 for X12 interchange) or in the group header fields would not cause interchange processing to fail.  
  
 If **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** is selected in agreement properties, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the transaction set if an error occurs. If **Split Interchange as Transaction Sets – suspend Interchange on Error** is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.  
  
 Each XML batch element is routed to the MessageBox, and processed by the send ports or orchestrations that subscribe to the batch element. The ordering of transaction sets in the interchange may not be retained after they are processed as split messages. On the receive side, the messages will be processed in the order that they appear in the interchange, and they will be placed in the MessageBox in that order, but you would have to use convoys or ordered delivery send ports to maintain that order on the send side.  
  
 If the elements split from a batch will be included in an outgoing batch, the BatchMarker pipeline component promotes the required properties. For more information, see [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).  
  
## See Also  
 [Processing Incoming Batches](../core/processing-incoming-batches.md)   
 [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md)