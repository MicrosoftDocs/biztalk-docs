---
title: "MLLP Receive and Send Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send components"
  - "Minimal Lower Layer Protocol (MLLP)"
  - "MLLP adapters"
  - "MLLP adapters, wrappers"
  - "wrappers [MLLP adapters]"
  - "receive components"
ms.assetid: 2f1c4099-8f52-437a-bdc1-efe707fbf347
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MLLP Receive and Send Components
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports all [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] native adapter types, including File, HTTP, SQL, and FTP. For HL7-encoded message receiving and sending, however, you typically use the MLLP adapter. This adapter is a TCP/IP socket adapter that uses the Minimal Lower Layer Protocol (MLLP). This protocol provides bi-directional message support and end-to-end health care application integration.  
  
 You can configure the MLLP receive adapter as either a two-way adapter or a one-way adapter. You can configure the MLLP send adapter as a two-way solicit-response send adapter, a one-way send adapter configured to receive acknowledgments (ACKs) on the same socket connection, or a one-way send adapter that does not return any messages. When you use the two-way solicit-response send MLLP adapter, you can configure the receive port to return either ACKs or response messages. For examples of MLLP send and receive adapters, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).  
  
 Messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives or sends on an MLLP adapter require the following wrappers:  
  
- \<SB\> Start Block character  
  
- \<EB\> End Block character  
  
- \<CR\> Carriage Return Byte (optional)  
  
  MLLP adapters provide error handling for missing \<SB\> or \<EB\> wrappers, dropped connections, or timeouts. With an MLLP adapter, you can configure a limitation on the number of connections. You can use an assortment of acknowledgments with an MLLP adapter.  
  
## See Also  
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [BizTalk Accelerator for HL7 Components](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)