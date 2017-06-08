---
title: "Processing an Incoming MDN | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd78e84c-4989-47e4-b95b-80582084ddec
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing an Incoming MDN
The AS2 receive pipelines (AS2EDIReceive and AS2Receive) process an incoming MDN based upon the agreement properties for the party as an AS2 message receiver. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically correlates the MDN to the outgoing AS2 message.  
  
 The steps each pipeline performs are as follows:  
  
-   Determines the sending party by matching the AS2-From value in the AS2 header of the message with the value for AS2-From list in the **Identifiers** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box. If a match is not found, the pipeline aborts processing and raises an exception.  
  
-   Promotes the following AS2 properties to the context:  
  
    -   IsAS2FailedMessage  
  
    -   DispositionType  
  
    -   GenerateAsynchronous200OKOnly  
  
    -   IsAS2MdnResponseMessage  
  
    -   IsAS2MessageSigned  
  
    -   OriginalMessageId  
  
    -   ReceivedContentMic  
  
    -   DispositionMode  
  
    -   MessageId  
  
-   Sets the InboundHttpHeaders property to all the HTTP headers of the message, and promotes it to the context of the message.  
  
-   Makes a copy of the MDN (in wire format), and stores the copy in the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database), if enabled in the one-way AS2 agreement properties.  
  
-   Performs MIME processing, including verifying the signature if the MDN was signed.  
  
-   Compares the MIC (Message Integrity Check) in the MDN with the MIC in the data store that was computed by the AS2Send pipeline when it sent out the original message (if applicable). For more information, see [MDN Messages](../core/mdn-messages.md).  
  
-   Makes correlation entries in the non-repudiation database.  
  
-   Deletes the MDN, unless the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.  
  
-   If the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box, the receive pipeline routes the MDN in wire format through the AS2 Decoder as a passthrough message and drops it into the MessageBox. The MDN in wire format contains all HTTP headers.  
  
    > [!NOTE]
    >  You can set up a send port to subscribe to a received MDN that has been dropped into the MessageBox. To subscribe to the received MDN, set the send port filter to `IsAS2MdnResponseMessage==True`.  
  
    > [!NOTE]
    >  If you use the AS2EdiReceive pipeline to process a received MDN, you cannot route the MDN into the MessageBox by setting the **Process inbound MDN into MessageBox for routing/delivery options** property in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box. Trying to do so will result in an EDI error because the MDN will be passed to the EDI Decoder, which cannot process an MDN. If the MDN is not sent to the MessageBox, the AS2Decoder will consume the MDN, so it will not be passed to the EDI Decoder.  
  
## Message Integrity Check  
 The Message Integrity Check (MIC) is used to verify that an MDN correlates to the original sent message. The AS2Send send pipeline calculates the MIC from the message payload when it generates the original AS2 message, and stores the MIC in the data store. When an MDN is required, the recipient of the original message generates an MIC and adds it to the MDN. When the AS2MdnReceive receive pipeline receives the MDN, if a signed MDN was requested, it compares the MIC in the MDN with the MIC in the data store.  
  
 A mismatch between the MIC in the MDN and the MIC in the data store indicates that there was an error during transmission or receipt of the message by the receiving party. The values reported in such a failure are the following:  
  
-   AS2DispositionType: Failed  
  
-   AS2DispositionModifierExtensionType: Error  
  
-   AS2DispositionModifierExtensionDescription: Integrity Check Failed  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)   
 [MDN Messages](../core/mdn-messages.md)