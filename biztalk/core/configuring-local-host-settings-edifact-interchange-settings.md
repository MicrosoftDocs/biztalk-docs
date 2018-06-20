---
title: "Configuring Local Host Settings (EDIFACT-Interchange Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1cf8696-d1f4-49aa-aa0a-ecf66f55e01d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Local Host Settings (EDIFACT-Interchange Settings)
The local host settings govern how the EDI interchanges are processed. The settings on this page can be divided into two categories – receiver’s settings (for incoming interchanges) and sender’s settings (for outgoing interchanges). As part of the receiver’s settings, you can specify whether an incoming batch will be split into transaction sets or preserved. If preserved, you can specify whether BizTalk Server suspends the interchange or transaction set if an error occurs. As part of the sender’s settings, you can specify how the control numbers are generated for outgoing messages.  
  
> [!IMPORTANT]
>  The following properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A.  
> 
> - All properties under the **Sender’s Settings** section.  
> 
>   Similarly, the following properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.  
> 
> - All properties under the **Receiver’s Settings** section.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure local host – receiver’s settings  
  
1. Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, under **Interchange Settings** section, click **Local Host Settings**.  
  
3. In the **EDIFACT ACK** section, to designate the transaction set reference numbers to be used in an acknowledgment, enter a value for the prefix, a range of reference numbers, and suffix.  
  
    Click **Reset** to reset the current transaction set reference number to the lower limit. Select **Reset to lower limit when out of bound** to have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reset the reference number to the lower range value limit if the maximum limit is exceeded.  
  
4. Clear the **Route ACK to send pipeline on request-response receive port** to return the acknowledgment via a separate send port. Leave the property selected to return the acknowledgment on the send port associated with the two-way request-response receive port.  
  
5. Clear **Mask security/authorization/password information** disable masking of authorization/password security information (the UNB6.1 and UNB6.2 fields) in the context property to prevent information disclosure.  
  
   > [!NOTE]
   >  When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives messages, it promotes the UNB header into the context of the message. Without masking, the security information within the context would be available to anyone with administrative privileges. To mask this information, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] replaces each character of the information with a **#** character. This is a one-way process: the **#** characters cannot be converted to actual characters.  
  
6. In the **Inbound batch processing option** drop-down, do the following:  
  
   1.  Select the default option **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets.  
  
   2.  Select **Split Interchange as Transaction Sets - suspend Interchange on Error** to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
   3.  Select **Preserve Interchange - suspend Interchange on Error** to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
   4.  Select **Preserve Interchange - suspend Transaction Sets on Error** to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets, while continuing to process all other transaction sets.  
  
       > [!NOTE]
       >  If you select **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**, the property settings on the **ISA Segment Definition** and **GS and ST Segment Definition** pages (which determine how BizTalk Server will create the ISA, GS, and ST headers of an outgoing interchange) do not apply. The interchange, group, and transaction-set headers that exist in the interchange that is being preserved are retained when the send pipeline processes it for sending.  
  
### To configure local host – sender’s settings  
  
1.  For **Interchange control number (UNB5)**, enter a range of values for the interchange control number to be used by BizTalk Server in generating an outgoing interchange. Enter a numeric value with a minimum of 1 and a maximum of 999999999. This is a mandatory field.  
  
    > [!NOTE]
    >  The first field (**UNB5.1**) is the prefix; the second and third fields (**UNB5.2**) contain the range of numbers to use as the interchange control number; and the fourth field (**UNB5.3**) is the suffix. The prefix and suffix are optional; the control number is required. The control number is incremented for each new message; the prefix and suffix remain the same. The maximum number of characters is 14 for the control number, 13 for the prefix and suffix, and 14 for all three fields combined.  
    >   
    >  To reset the control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
2.  For **Group control number (UNG5)**, enter the prefix, reference number range, and suffix that BizTalk Server should use for the group control number of the first interchange that it sends.  
  
    > [!NOTE]
    >  The first field (**UNG5.1**) is the prefix; the second and third fields (**UNG5.2**) contain the range of numbers to use for the group control number; and the fourth field (**UNG5.3**) is the suffix. The prefix and suffix are optional; the control number is required. The control number is incremented for each new message until the maximum value is reached; the prefix and suffix remain the same. Only numbers are allowed in **UNG5.2**. The maximum number of characters is 14 for the control number, 13 for the prefix and suffix, and 14 for all three fields combined.  
    >   
    >  To reset the group control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
3.  For **Message Header (UNH)**, click **Apply new ID**, enter the prefix, enter the reference number range, and enter the suffix that BizTalk Server should use for the transaction set reference number.  
  
    > [!NOTE]
    >  The first field (**UNH1.1**) is the prefix; the second and third fields (**UNH1.2**) are the reference number range; and the fourth field (**UNH1.3**) is the suffix. The prefix and suffix are optional; the reference number is required. The reference number is incremented for each new message; the prefix and suffix remain the same. The default value range for the reference number is 1 to 99999999999999. Only numbers are allowed in **UNH1.2**. The maximum number of characters is 14 for the control number, 13 for the prefix and suffix, and 14 for all three fields combined.  
    >   
    >  To reset the current transaction set control number to the minimum value, click **Reset**. Select **Reset to lower limit when out of bound** to reset the control number to the minimum value if the maximum value has been exceeded.  
  
4.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (EDIFACT)](../core/configuring-interchange-settings-edifact.md)