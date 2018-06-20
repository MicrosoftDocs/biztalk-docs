---
title: "Agreement Resolution for Outgoing AS2 Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 578d7565-534c-4c13-b473-975f347f3a9b
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agreement Resolution for Outgoing AS2 Messages
When an AS2 send pipeline processes an outgoing EDIINT/AS2-encoded message over HTTP/HTTPS transport, it determines the agreement that the message will resolve to. It will then use those agreement properties to process the outgoing message. The send pipeline will use the following criteria to determine the agreement (in order of priority):  
  
1. The send pipeline attempts to match the AS2From and AS2To context properties with the values of AS2From and AS2To specified as part of the agreement properties.  
  
2. If the previous step fails, the send pipeline will attempt to match the AS2To context property of the outbound message with the value of AS2To property, which is set as additional agreement resolver in the **Identifiers** tab of agreement properties.  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not write the AS2To property to the context. If you want to perform agreement resolution on the AS2To context property, you will have to incorporate a custom orchestration or a custom pipeline component to do so. For more information, see [Writing AS2 Context Properties for Outbound Party Resolution](../core/writing-as2-context-properties-for-outbound-party-resolution.md).  
   > 
   > [!NOTE]
   >  When you are using a dynamic send port, the AS2To property must be written to the context for agreement resolution.  
  
3. If the previous step fails, the send pipeline will attempt to match the send port that is associated with an agreement with the send port that subscribed to the message. The send port is associated with the agreement in the **Send Ports** page of the one-way AS2 agreement of the **Agreement Properties** dialog box.  
  
   > [!NOTE]
   >  Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement. There is, however, a default agreement used to send an MDN. In addition, neither the send port nor the Http.UserHttpHeaders context property is used to resolve the agreement for an MDN. For more information, see the "Agreement Resolution for an MDN" section of [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).  
   > 
   > [!NOTE]
   >  If the AS2-To agreement property in the **Identifiers** page of the one-way AS2 agreement of the **Agreement Properties** dialog box is set by default to an English party name, and the value in the AS2-To header of the AS2 message is set to a non-English name, then the match will not be found.  
  
> [!NOTE]
>  When sending EDI over AS2, you are required to use separate agreements for both EDI and AS2.  
  
 For more details on the send process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).  
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)