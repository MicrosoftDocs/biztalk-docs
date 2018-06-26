---
title: "Configuring Validation (AS2) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ff22dc8-a544-46f9-86fb-f6845e2dfe46
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Validation (AS2)
In the partner agreement, you must specify the validation settings to validate the inbound AS2 message.  
  
> [!NOTE]
>  No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, the following properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
>   
>  -   **Use agreement settings for validation and MDN instead of message header**  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure validation properties  
  
1. Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, click **Validation**.  
  
3. Select the **Use agreement settings for validation and MDN instead of message header** check box if you want [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validate the digital signature, compression, and encryption of the incoming message, based upon the settings in the agreement. If the check box is cleared, the messages will be validated against the properties in the message AS2 header instead of the agreement properties to determine this processing. For a list of AS2 headers, see [AS2 Messages](../core/as2-messages.md).  
  
4. Select the **Message should be signed** check box to ensure that the inbound message is signed.  
  
5. Select the **Message should be compressed** check box to ensure that the inbound message is compressed.  
  
6. Select the **Message should be encrypted** check box to ensure that the inbound message is encrypted. Select the encryption algorithm from the **Encryption Algorithm** drop-down list. 

   **Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] and newer versions**, AES support is automatically included. Options include DES3, RC2, AES128 (default), AES192, and AES256.
    
   For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, the options are DES3 and RC2.
  
   > [!NOTE]
   >  Only if the appropriate property is set, the AS2 receive pipeline verifies the digital signature, decompresses the message, or decrypts the message. If the **Use agreement settings for validation and MDN instead of message header** property is selected and the message has different transport properties for signing, compression, and encryption than those selected on the agreement properties, then the AS2 Decoder will suspend the message and post an error.  
  
7. Select the **Check Certification Revocation List** check box to determine whether the certificate to be used in validating an incoming message has been included in the Certification Revocation List, indicating that it has been revoked, or whether the expiration date has passed. If so, BizTalk Server will not decrypt the message, but will suspend it. If this property is cleared, BizTalk Server will not perform this check.  
  
   > [!NOTE]
   >  There is a latency involved with retrieving and searching the certificate revocation list.  
  
8. Select the **Check for duplicate messages within** check box to determine if the incoming message is a duplicate of previously received messages.  
  
    If you checked the **Check for duplicate messages within** property, set the **days** property to indicate the span of previously received messages to use when checking for duplicates; check the **Suspend duplicate messages** property to indicate that duplicate messages should be suspended.  
  
   > [!NOTE]
   >  The **AS2-From** and **AS2-To** fields are used to determine if a message is a duplicate. If the message contains the same values for these fields as a previously received message, it will be marked as duplicate even if the other headers or the payload is different.  
  
9. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md)