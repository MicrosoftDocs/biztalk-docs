---
title: "Configuring Acknowledgements (EDIFACT) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9436feb7-4c29-4b7c-b5c2-991660e6c1a9
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Acknowledgements (EDIFACT)
In the partner agreement, you can specify what type of acknowledgment to return to a party and what kind of send port to use in sending the acknowledgment. You also specify whether to batch an acknowledgment, what the starting transaction set reference number is for the acknowledgment, and whether SG1/SG4 loops are generated for accepted transaction sets.  
  
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **Generate SG1/SG4 loop for accepted transaction sets (If unchecked, loop will be generated only if UCM.5 is not equal to 7)**.  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure EDIFACT ACK (CONTRL) properties  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Interchange Settings** section, click **Acknowledgements**.  
  
3.  In the **EDIFACT ACK (Control) section**, do the following:  
  
    1.  Select **Receipt of message (CONTRL) expected** to return a technical (CONTRL) acknowledgment to the interchange sender. If **Receipt of message (CONTRL) expected** is selected, select **Do not batch receipt of message (CONTRL) message** to send each acknowledgment separately, or leave cleared to batch the acknowledgments.  
  
    2.  Select **Acknowledgement (CONTRL) expected** to return a functional (CONTRL) acknowledgment to the interchange sender. If **Acknowledgement (CONTRL) expected** is selected, select **Do not batch Acknowledgement (CONTRL)** to send each functional acknowledgment separately, or leave cleared to batch the functional acknowledgments.  
  
4.  In the **Transaction set status acceptance reporting** section, to force generation of SG1/SG4 loops in functional CONTRL acknowledgments for accepted transaction sets, select **Generate SG1/SG4 loop for accepted transaction sets (If unchecked, loop will be generated only if UCM.5 is not equal to 7)**. For more information about SG1/SG4 loops, see [EDIFACT CONTRL Message as Functional Acknowledgment](../core/edifact-contrl-message-as-functional-acknowledgment.md).  
  
5.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (EDIFACT)](../core/configuring-interchange-settings-edifact.md)