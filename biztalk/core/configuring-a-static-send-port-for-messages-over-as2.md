---
title: "Configuring a Static Send Port for Messages over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2708d6a9-b105-42d3-abe3-7085b39da55a
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring a Static Send Port for Messages over AS2
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send AS2 messages over a static send port. This configuration includes creating the static send port and configuring the agreement. If required, you will also set up an encryption certiticate to be used by the send port.  
  
> [!NOTE]
>  You can configure a dynamic send port to send AS2 messages, instead of a static send port. For more information, see [Configuring a Dynamic Send Port for Messages over AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md).  
  
 To send an AS2 message with an EDI or non-EDI message or an EDI acknowledgment, create a solicit response HTTP send port with the following configuration:  
  
|Location|Property|Setting|  
|--------------|--------------|-------------|  
|**Send Port Properties: General**|Port Type|- Static Solicit Response (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)<br /><br /> - Static One-way Send Port (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is cleared)|  
|**Send Port Properties: General**|Transport Type|HTTP<br /><br /> Note:<br /><br /> Only the HTTP adapter can be used for transporting EDIINT/AS2-encoded messages. This transport will not work with an adapter other than the HTTP adapter.|  
|**Send Port Properties: General**|Send handler|BizTalkServerApplication|  
|**Send Port Properties: General**|Send pipeline|- AS2EdiSend (for EDI-encoded messages)<br /><br /> - AS2Send (for non-EDI messages)|  
|**Send Port Properties: General**|Receive handler<br /><br /> (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)|BizTalkServerApplication|  
|**Send Port Properties: General**|Receive pipeline<br /><br /> (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)|AS2Receive|  
|**HTTP Transport Properties**|Destination URL|\<Destination URL string\>|  
|**HTTP Transport Properties**|Enable chunked encoding|Cleared|  
|**Send Port Properties: Filters**|Property|BTS.MessageType<br /><br /> Note:<br /><br /> You can use a variety of filter expression, including using BTS.ReceivePortName.<br /><br /> Note:<br /><br /> For non-EDI messages, you will have to filter on a different property)|  
|**Send Port Properties: Filters**|Operator|==|  
|**Send Port Properties: Filters**|Value|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>` (for an EDI message)<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root` (for an X12 acknowledgment)<br /><br /> -                   `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root` (for an EDIFACT acknowledgment)|  
|**Send Port Properties: Certificates**|Common Name  and thumbprint|Enter the certificate name and thumbprint if using an encryption certificate for the outbound AS2 message.|  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure BizTalk Server to send AS2 messages over a static send port  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a static one-way or solicit response send port with the above configuration.  
  
2. In the send ports list on the **Send Ports** page of the one-way agreement tab in the **Agreement Properties** dialog box, enter the name of the static send port.  
  
   > [!NOTE]
   >  Setting the send port enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform agreement resolution for an outbound AS2 message.  
  
3. In the **Identifiers** page of the one-way agreement tab of the **Agreement Properties** dialog box, set the AS2-To property to the destination and then set other agreement properties as required in the different pages of the **Agreement Properties** dialog box.  
  
## Functionality  
 The send port and pipeline does the following to send a synchronous EDI or non-EDI message or acknowledgment over AS2 and process the returned MDN:  
  
-   If sending an EDI message, picks up the EDI message by filtering on the property `BTS.MessageType` set to the message schema in the `http://schemas.microsoft.com/BizTalk/EDI/X12/2006` namespace (for example, X12_00401_864 for an 864 message).  
  
-   If sending an EDI acknowledgment, picks up the acknowledgment by filtering on the property `BTS.MessageType` set to one of the following control schema:  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root` for a 997 acknowledgment  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root` for a TA1 acknowledgment  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root` for a CONTRL acknowledgment  
  
-   If sending a non-EDI message, picks up the message using another filter.  
  
-   Builds an AS2 message. For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
-   Sends the message or acknowledgment to the destination URL for the send port.  
  
-   Receives the MDN response to the message or acknowledgment, if enabled. For more information about this process, see [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md).  
  
## See Also  
 [Configuring Ports for an AS2 Solution](../core/configuring-ports-for-an-as2-solution.md)   
 [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md)   
 [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md)