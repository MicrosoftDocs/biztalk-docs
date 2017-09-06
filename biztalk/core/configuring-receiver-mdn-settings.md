---
title: "Configuring Receiver MDN Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eae6431d-a2b9-4889-a29c-720e801a644e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Receiver MDN Settings
As part of receiver MDN settings, you can specify the properties that govern MDN generation based on the AS2 message header.  
  
> [!IMPORTANT]
>  No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure receiver MDN settings  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Local Host Settings** section, click **Receiver MDN Settings**.  
  
3.  If you did not check the **Use agreement settings for validation and MDN instead of message header** property in the **Validations** page, you can choose to have the party sending the MDN, sign the MDN if generation of the MDN is enabled by the **Disposition-Notification-to** AS2 header, but the **Disposition-Notification-Options** header does not enable signing. This can occur if **Disposition-Notification-Options** is either not set or is set to optional. You can do so by clicking **Sign requested MDN if Disposition-Notification-Option header is not preset or if Signed-Receipt-Protocol header is set to optional**.  
  
4.  You can enter a text in the **MDN Text** field to have the party sending the MDN add it to the MDN message (under the Content-Description field). This setting is applicable irrespective of whether the MDN was generated based upon the AS2 headers or the agreement properties.  
  
5.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)