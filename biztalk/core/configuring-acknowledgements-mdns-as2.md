---
title: "Configuring Acknowledgements (MDNs) (AS2) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb2bf98a-deb4-460f-a1fc-3d2397c39470
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Acknowledgements (MDNs) (AS2)
In the partner agreement, you can specify how the party receiving the AS2 message generates an MDN response and sends it to back.  
  
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **Resend AS2 message if MDN not received** check box and associated properties  
>   -   **Override send port settings** check box and associated properties  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure acknowledgements  
  
1. Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md). To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, click **Acknowledgements (MDNs)**.  
  
3. Select the **Process inbound MDN into MessageBox for routing/delivery options** check box to route the MDN through the A2 Decoder as a passthrough message and then into the MessageBox. When this property is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] promotes the `IsAS2MdnResponseMessage` property for routing purposes.  
  
4. If you checked the **Use agreement settings for validation and MSDN instead of message header** property in the **Validations** page, select the **Request MDN** check box if the trading partner must generate an MDN in response to the AS2 message.  
  
    If the **Request MDN** check box is selected, you can also set the following properties:  
  
   1. Select the **Request signed MDN** check box and from the **Signing Algorithm** drop-down select the MIC algorithm that the trading partner must use to sign the MDN. [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] supports MD5, SHA1, and SHA2 (SHA256 (default), SHA384, and SHA512).
    
      > [!NOTE]
      > **Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] and newer versions**, SHA2 support is automatically included. For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, see [KB 3123748](https://support.microsoft.com/kb/3123748).
  
   2. Select the **Request asynchronous MDN** check box and then in the **Receipt-Delivery-Option (URL)** text box, enter the URL that the receiving party should send the MDN to.  
  
       If the **Request asynchronous MDN** check box is selected, you can also set the following properties:  
  
      1. Select the **Resend AS2 message if MDN not received** check box to enable retransmission of the AS2 message. Enter a value for **Minimum AS2 message resend interval**, **Number of AS2 message resend attempts** and **Stop attempting AS2 message resends after** fields to specify the retry interval, maximum number of attempts and when to stop resending the message.  
  
         > [!NOTE]
         >  You must select the **Turn ON Reporting** check box on the **General Properties** page of the **General** tab before selecting **Resend AS2 message if MDN not received**.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses tracking information stored for AS2 reporting in order to determine when to resend an AS2 message.  
  
      2. If **Resend AS2 message if MDN not received** check box is selected, check **Override send port settings** to specify the **Minimum HTTP retry interval** and **Number of HTTP retry attempts**. Enter a value for the **Stop attempting HTTP retries after** field to specify the maximum amount of time to attempt retries using the HTTP adapter.  
  
   3. If you selected the **Request asynchronous MDN** check box and specified a URL for **Receipt-Delivery-Option (URL)** property, the **Disposition-Notification-To** text box, is by default set to the same URL. If you did not select the **Request asynchronous MDN** check box, you must enter a value for **Disposition-Notification-To**. The value of this field is not used during AS2 processing.  
  
5. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md)