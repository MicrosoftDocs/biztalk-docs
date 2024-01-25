---
description: "Learn more about: Configuring General Local Host Settings (AS2)"
title: "Configuring General Local Host Settings (AS2)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring General Local Host Settings (AS2)
As part of the local host general settings, you can specify the content type of the AS2 messages and whether the file name is preserved as part of the AS2 message header.  
  
> [!IMPORTANT]
>  All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
>   
>  The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure the general settings  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Local Host Settings** section, click **General**.  
  
3.  Select the **Check Certification Revocation List before sending the message** check box to determine whether the certificate to be used in signing an outgoing messages has been included in the Certification Revocation List, indicating that it has been revoked, or whether the expiration date has passed. If so, BizTalk Server will not encrypt the message, but will suspend it. If this property is cleared, BizTalk Server will not perform this check.  
  
    > [!NOTE]
    >  There is a latency involved with retrieving and searching the certificate revocation list.  
  
4.  For **Default content type**, select the default content type that the party must use for an outgoing AS2 message. If the `ContentType` property is set in the context for a message body part, that setting is used to generate the outgoing message; otherwise, the value of this **Default content type** property is used.  
  
5.  Select the **Transmit file name in MIME header** check box to send a file name as part of the MIME header for the outbound AS2 message. To specify the file name, select **Specify file name** or **Have system generate file name**.  
  
    > [!NOTE]
    >  Selecting **Have system generate file name** will generate a new GUID value as the file name of each attachment sent in the AS2 message.  
  
6.  If you selected **Specify file name**, enter a string value or context property in the **Specify file name** field. You can also enable **Suspend message if context property (e.g. %property%) not found** to suspend the message if the selected context property does not exist for the outbound message.  
  
    > [!NOTE]
    >  To specify a context-property, enclose the property name with the % character. For example, `%FILE.ReceivedFileName%`.  
  
7.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)
