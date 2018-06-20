---
title: "Configuring Acknowledgements (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eec2dbff-5d04-4a38-bad0-33d040b6dd12
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Acknowledgements (X12)
In the partner agreement, you can specify how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates acknowledgments in response to X12-encoded interchanges received from the party and what type of acknowledgment to return to a party. You can also specify whether to batch an acknowledgement and whether AK2 loops are generated for accepted transaction sets. This section provides instructions on how to do so.  
  
> [!NOTE]
>  The acknowledgement properties described here apply also for HIPAA acknowledgements.  
> 
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**.  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure X12 ACK properties  
  
1.  Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Interchange Settings**, click **Acknowledgements**.  
  
3.  Select **TA1 Expected** to return a technical (TA1) acknowledgment to the interchange sender. If selected, select **Do not batch TA1** to send each technical acknowledgment separately, or leave the check box cleared to batch the technical acknowledgments.  
  
4.  Select **997 Expected** to return a functional (997) acknowledgment to the interchange sender. If selected, select **Do not batch 997** to send each functional acknowledgment separately, or leave the check box cleared to batch the functional acknowledgments.  
  
5.  To enable generation of AK2 loops in 997 acknowledgments for accepted transaction sets, select **Include AK2 loop for accepted transaction sets (if unchecked, loop will be generated only if AK501 is not equal to A)**. For more information about AK2 loops, see [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md).  
  
6.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md)