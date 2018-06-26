---
title: "Configuring General Party Properties (AS2) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9a4dbd0-8849-403a-af82-58ee0b10f85a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring General Party Properties (AS2)
A party or trading partner represents a participating organization in a business relationship. Party properties contain the following information:  

- General information such as party name  

- Send ports associated with the party  

- Certificates associated with the party  

  For more information about parties or trading partners, see [Trading Partners](../core/trading-partners-and-business-profiles.md).  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

### To configure party properties  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  

2. On the **General** page of the **Party Properties** dialog box, do the following:  


   |                                                Use this                                                 |                                                                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                                                                       |
   |---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                **Name**                                                 |                                                                                                                                                                                                                                                                  Enter a party name.                                                                                                                                                                                                                                                                  |
   | **Local BizTalk processes messages received by the party or supports sending messages from this party** | Select this checkbox to specify that the party represents the same trading partner that also hosts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. **Important:**  For a two-party TPM solution that uses out-of-the-box pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must select this check box for at least one party. **Note:**  If you clear this check box, some properties will be disabled while creating the agreements for this party. |
   |                                **Additional Properties – Name / Value**                                 |                                                                                                                                                Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want. **Note:**  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.                                                                                                                                                 |
   |                                               **Delete**                                                |                                                                                                                                                                                                                                                     Click to delete the selected name-value pair.                                                                                                                                                                                                                                                     |


3. On the **Send Ports** page of the **Party Properties** dialog box, do the following:  

   > [!NOTE]
   >  In BizTalk Server, the send port association is done at the agreement level. The **Send Ports** page available as part of the party properties is purely for backward compatibility. Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well. However, the reverse is not true. You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings. For more information on how to associate send ports with agreement, see here.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Send ports - Name**|From the drop-down list, select a send port to bind to this party.|  
   |**Send ports - URI**|Displays the send port address.|  
   |**Remove**|Click to remove the selected send port from the party.|  
   |**Properties**|Click to display the **Send Port Properties** dialog box for the selected send port.|  

   > [!NOTE]
   >  BizTalk Server can determine the party to send the message to by matching the send port that subscribes to the message with the send port associated with a party. It can also do so using context properties. For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  

4. On the **Certificate** page, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Browse**|Click to display the **Select Certificate** dialog box, where you select the signature certificate from the Local Machine or Other People certificate store to apply to messages transmitted to the party.|  
   |**Common Name**|Displays a description of the selected certificate.|  
   |**Thumbprint**|Displays the thumbprint of the private key certificate that is used for party resolution and signature verification. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).|  
   |**Remove certificate**|Click to remove the displayed certificate.|  

   > [!NOTE]
   >  The certificate you specify for a party is used to verify signature of an AS2 message or MDN from the party. The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties. For more information on certificates used with AS2 messages, see [AS2 Security](../core/as2-security.md). You may need to install and define certificates for outbound signing, inbound signature verification, outbound encryption, and inbound decryption.  

5. Click **Apply** to accept the properties, or click **OK** to complete the configuration setting. Either action will validate the settings.  

## See Also  
 [Configuring AS2 Properties](../core/configuring-as2-properties.md)