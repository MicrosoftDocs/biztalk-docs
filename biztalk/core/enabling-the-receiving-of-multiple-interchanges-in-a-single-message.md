---
title: "Enabling the Receiving of Multiple Interchanges in a Single Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c98bcd2e-495a-49d8-a471-6e23b1e161f9
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enabling the Receiving of Multiple Interchanges in a Single Message
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can process a message that contains multiple interchanges. For an X12 message, such a message would include multiple ISA headers and IEA trailers. For an EDIFACT message, such a message would include multiple UNA/UNB headers and UNZ trailers.  
  
 To enable the EDI Disassembler in the EdiReceive or AS2EdiReceive pipeline to parse multiple interchanges in a single message, you must set the **DetectMID** pipeline property to **True**. (MID stands for multiple interchange disassembling.) This property is set to True by default.  
  
 When the receive pipeline that includes the EDI Disassembler receives a message with multiple interchange, the Disassembler will parse each interchange from the interchange header to the interchange trailer. This processing is done according to the following rules:  
  
- All interchanges in the same message must be of the same encoding type, either X12 or EDIFACT. If the message contains interchanges of more than one encoding type, the EDI Disassembler will process all interchanges that have the same encoding type as the first interchange in the message. The Disassembler will ignore all interchanges that are of a different encoding type from the first interchange.  
  
- The EDI Disassembler will ignore any character between the interchange trailer of one interchange and the interchange heading of the next interchange.  
  
- If you enable authentication by selecting either the **Drop messages if authentication fails** or the **Keep messages if authentication fails** property for the receive port, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the entire message if any one of the multiple interchanges in the message fails.  
  
- If you enable authentication, and if any one interchange in the same message does not resolve to an agreement, then all interchanges in the message will be suspended, and no acknowledgments will be returned, even for those interchanges that did resolve to an agreement.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To enable the receiving of multiple interchanges in a message  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Receive Locations** node, right-click the receive location that you want to enable to receive multiple interchange in a single message, and then click **Properties**.  
  
2. Click the ellipses next to the receive pipeline (which must be either EdiReceive or AS2EdiReceive).  
  
3. In the **Configure Pipeline** dialog box, set the **DetectMID** pipeline property to **True**.  
  
4. Click **OK**, then click **OK** again.  
  
## See Also  
 [Configuring Ports for an EDI Solution](../core/configuring-ports-for-an-edi-solution.md)