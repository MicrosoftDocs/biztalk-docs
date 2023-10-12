---
description: "Learn more about: Configuring Sender Message Tracking (NRR)"
title: "Configuring Sender Message Tracking (NRR)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring Sender Message Tracking (NRR)
As part of the settings on this page, you can specify whether the outbound messages and their acknowledgements (MDNs) are stored in the non-repudiation database. For more information, see [AS2 Processing in BizTalk Server](../core/as2-processing-in-biztalk-server.md).  
  
 To store messages in the non-repudiation database, the parties must enable NRR (Non-repudiation of receipt) as part of the AS2 agreement properties. NRR ensures that the sender party has verified the signed receipt from the message recipient. Conceptually, an NRR is an undeniable proof for the message sender that the message reached the destination unaltered. NRR can be established only when the original message and the receipt are digitally signed.  
  
> [!IMPORTANT]
>  All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
>   
>  The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure message tracking for outbound AS2 messages and inbound MDN  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Local Host Settings** section, click **Sender Message Tracking (NRR)**.  
  
    > [!NOTE]
    >  To guarantee non-repudiation of receipt, you must establish the authentication and integrity of the message. The recommended way of doing so is by using a digital signature on the message. As a result, if you select any of the properties to store messages in the non-repudiation database, you should sign the message by selecting the **Message should be signed** property on the **Validation** page.  
  
3.  Select **NRR enabled for outbound encoded AS2 messages** to store outbound encoded AS2 messages in the non-repudiation database.  
  
4.  Select **NRR enabled for outbound decoded AS2 messages** to store outbound decoded AS2 messages in the non-repudiation database.  
  
5.  Select **NRR enabled for inbound MDN** to store inbound MDN in the non-repudiation database.  
  
6.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)
