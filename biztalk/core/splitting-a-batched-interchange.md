---
title: "Splitting a Batched Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e67bef19-77fb-47a9-88f3-ee20043b3691
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Splitting a Batched Interchange
This topic describes how to configure an agreement for processing a batched EDI interchange by splitting the transaction sets from the interchange.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To receive a split EDI interchange  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node. In the **Parties and Business Profiles** page, click the party that has the agreement that will resolve to the incoming batched interchange. In the **Agreement** section of the page, right-click the agreement and click **Properties**. In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound batched interchange will resolve), do the following:  
  
   1.  In the **Identifiers** page, make sure you enter the correct values so that the incoming batched interchange resolves to this agreement.  
  
       -   In case of **X12**: Set ISA5, ISA6, ISA7, and ISA8.  
  
       -   In case of **Edifact**: Set UNB2.1, UNB2.2, UNB3.1, and UNB3.2.  
  
   2.  In the **Local Host Settings** page (under **Interchange Settings**), under **Receiver’s Settings** section, for the **Inbound batch processing option**, select one the following options:  
  
       -   **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets.  
  
       -   **Split Interchange as Transaction Sets - suspend Interchange on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
2. Create a Visual Studio project for the preserved batch as follows:  
  
   1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a BizTalk project and add the schemas for all the messages within the batch.  
  
   2. Build and deploy the project.  
  
3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a send port to send split batches as follows:  
  
   1.  Set the send pipeline to **EdiSend** or **AS2EdiSend**.  
  
   2.  Set the filter of the send port to the value required to pick up each transaction set, for example, to BTS.MessageType.  
  
## See Also  
 [Configuring EDI Batches](../core/configuring-edi-batches.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)