---
title: "Preserving a Batched Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 907e07f3-1f3e-485e-a82d-b28eb7658e0a
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preserving a Batched Interchange
This topic describes how to configure an agreement for processing a batched EDI interchange as a single document without splitting the transaction sets from the interchange.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure the receiving and sending of a preserved batch  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node. In the **Parties and Business Profiles** page, click the party that has the agreement that will resolve to the incoming batched interchange. In the **Agreement** section of the page, right-click the agreement and click **Properties**. In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound batched interchange will resolve), do the following:  
  
   1.  In the **Identifiers** page, enter the values for enter values for ISA5, ISA6, ISA7, and ISA8. Make sure you enter the correct values so that the incoming batched interchange resolves to this agreement.  
  
   2.  In the **Local Host Settings** page (under **Interchange Settings**), under **Receiver’s Settings** section, for the **Inbound batch processing option**, select one the following options:  
  
       -   **Preserve Interchange - suspend Interchange on Error** – Select this option to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
       -   **Preserve Interchange - suspend Transaction Sets on Error** – Select this option to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets, while continuing to process all other transaction sets.  
  
       > [!NOTE]
       >  If you select either of the two options mentioned above, the interchange, group, and transaction set segment properties (which determine how BizTalk Server will create the ISA, GS, and ST headers of an outgoing interchange) do not apply. The interchange, group, and transaction-set headers that exist in the interchange that is being preserved are retained when the send pipeline processes it for sending. However, if you do want to use the values specified for the interchange in the agreement, set the `EDI.PopulateInterchangeValues` context property to true.  
  
2. Create a Visual Studio project for the preserved batch as follows:  
  
   1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a BizTalk project and add the schemas for all the messages within the batch.  
  
   2. Build and deploy the project.  
  
3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a send port to send preserved batches as follows:  
  
   1.  Set the send pipeline to **EdiSend** or **AS2EdiSend**.  
  
   2.  Set the filter of the send port to the context property `EDI.ReuseEnvelope == True`.  
  
       > [!NOTE]
       >  Setting this filter ensures that the send port will subscribe to all batched interchanges that are preserved. The EdiReceive receive pipeline promotes the context property `EDI.ReuseEnvelope` to identify the interchange as preserved.  
  
## See Also  
 [Configuring EDI Batches](../core/configuring-edi-batches.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)