---
description: "Learn more about: Configuring Signature Certificates (AS2)"
title: "Configuring Signature Certificates (AS2)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configuring Signature Certificates (AS2)
As part of the settings on this page, you can specify the certificates to be used for signing all outgoing messages and MDN that resolve to this agreement. The settings on this page override the certificate settings provided as part of the BizTalk Group properties. For more information on how certificates are used, see [Configuring Certificates for AS2](../core/configuring-certificates-for-as2.md).  
  
> [!IMPORTANT]
>  No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure agreement-level signature certificate  
  
1.  Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, click **Signature Certificates**.  
  
3.  Select the **Override group signing certificate** check box to use the certificate provided in this page for signing outgoing AS2 messages and MDN.  
  
4.  Click **Browse** to display the **Select Certificate** dialog box, where you select the signature certificate to apply to messages transmitted by this party.  
  
5.  The **Common Name** text box displays a description of the selected certificate.  
  
6.  The **Thumbprint** text box displays the thumbprint of certificate. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).  
  
7.  Click **Remove Certificate** to remove the selected certificate.  
  
8.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md)
