---
title: "Configuring Global or Fallback Agreement Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c375d03-6f22-4a67-9eac-d8896de2f7ee
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Global or Fallback Agreement Properties
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses fallback agreement properties to process a message when it does not discover an agreement to resolve to for an interchange. Fallback agreement properties are not used when the agreement is known, and do not apply to any or all agreements.  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it attempts to match the sender information for an agreement with the sender information in the message. The sender information is in the ISA5 and ISA6 data elements for X12 message, and the UNB2.1 and UNB 2.2 data elements for EDIFACT. The agreement information is in the Identifier tabs in the one-way agreement tab of the **Agreement Properties** dialog box. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not discover the agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to determine the namespace, process the message, and send any acknowledgments.  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a message, the EDI send pipeline determines the agreement that the message resolves to by matching the send port that subscribes to the XML message in the MessageBox, with the send port associated with the agreement. If the send port is not associated with an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to process the message for sending.  
  
> [!NOTE]
>  Send port association is only one way of doing agreement resolution. For more information about agreement resolution for outgoing messages, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
## In This Section  
  
-   [Configuring X12 Fallback Agreement Properties](../core/configuring-x12-fallback-agreement-properties.md)  
  
-   [Configuring EDIFACT Fallback Agreement Properties](../core/configuring-edifact-fallback-agreement-properties.md)  
  
## See Also  
 [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md)