---
title: "Configuring a Dynamic Send Port for Messages over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 246d64e8-70ca-48f4-8b72-d43b0964dbb4
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Dynamic Send Port for Messages over AS2
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send AS2 messages over a dynamic send port. This configuration includes creating the dynamic send port and configuring a backend application to set the appropriate context properties. When you create a dynamic send port to send an AS2 message, you must promote certain properties for the send port to work. For more information, see [To configure BizTalk Server to send AS2 messages over a dynamic send port](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md#BKMK_Proc) below.  
  
 A dynamic send port enables you to send messages to multiple parties without hard-coding the party configuration. The agreement and destination to be used in sending the message are determined dynamically through context properties. You do not have to create a static send port for each individual customer.  
  
 To send an AS2 message with an EDI or non-EDI message or an EDI acknowledgment, create a dynamic response HTTP send port with the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port Type|- Dynamic Solicit Response (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)<br /><br /> - Dynamic One-way Send Port (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is cleared)|  
|**Send Port Properties: General**|Send pipeline|- AS2EdiSend (for EDI-encoded messages)<br /><br /> - AS2Send (for non-EDI messages)|  
|**Send Port Properties: General**|Receive pipeline<br /><br /> (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)|AS2Receive (for dynamic solicit response send port)|  
|**Send Port Properties: Filters**|Property|BTS.MessageType|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>` (for an EDI message)<br /><br /> - `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root` (for an X12 acknowledgment)<br /><br /> - `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root` (for an EDIFACT acknowledgment)|  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
##  <a name="BKMK_Proc"></a> To configure BizTalk Server to send AS2 messages over a dynamic send port  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a dynamic one-way send port (if an MDN is not requested) or a dynamic solicit response send port (if an MDN is requested) with the above configuration.  
  
2. For the agreement that applies to this message, set the AS2 and EDI properties required.  
  
3. Promote the following properties to the message context:  
  
   -   `BTS.MessageType`  
  
   -   `EdiIntAS.MessageID`  
  
4. Add functionality to a backend application to write the following properties to the message context, setting them to the appropriate values:  
  
   -   `EdiIntAS.AS2To`  
  
   -   `BTS.OutboundTransportLocation`  
  
   -   `HTTP.EnableChunkedEncoding`  
  
   -   `BTS.EncryptionCert`  
  
   > [!NOTE]
   >  The `AS2To` context property and the `OutboundTransportLocation` context property must be written to the message context for the dynamic send port to function properly. The `AS2To` property is required for the port to determine the agreement to use in processing the outgoing message and the `OutboundTransportLocation` property is required for the send port to determine the destination of the message. For more information, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
## Functionality  
 The dynamic send port and pipeline does the following to send a synchronous EDI or non-EDI message or acknowledgment over AS2 and process the returned MDN:  
  
- If sending an EDI message, picks up the EDI message by filtering on the property `BTS.MessageType` set to the message schema in the `http://schemas.microsoft.com/BizTalk/EDI/X12/2006 namespace` (for example, X12_00401_864 for an 864 message).  
  
- If sending an EDI acknowledgment, picks up the acknowledgment by filtering on the property `BTS.MessageType` set to one of the following control schema:  
  
  -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root` for a 997 acknowledgment  
  
  -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root` for a TA1 acknowledgment  
  
  -   `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root` for a CONTRL acknowledgment  
  
- If sending a non-EDI message, picks up the message using an appropriate filter.  
  
- Builds an AS2 message. For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
  > [!NOTE]
  >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the transport type to be used by the dynamic send port from the format of the URL, i.e., http, smtp, ftp, etc.  
  
- Routes the message or acknowledgment to the destination URL for the send port.  
  
- Receives the MDN response to the message or acknowledgment, if enabled and if a solicit-response send port. For more information about this process, see [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md).  
  
## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)