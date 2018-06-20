---
title: "Configuring Local Host Settings (X12-Interchange Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c66c1e63-c654-4ccb-b424-34c06f1ce94e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Local Host Settings (X12-Interchange Settings)
The local host settings govern how the EDI interchanges are processed. The settings on this page can be divided into two categories – receiver’s settings (for incoming interchanges) and sender’s settings (for outgoing interchanges). As part of the receiver’s settings, you can specify whether an incoming batch will be split into transaction sets or preserved. If preserved, you can specify whether [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspends the interchange or transaction set if an error occurs. As part of the sender’s settings, you can specify how the control numbers are generated for outgoing messages  
  
> [!NOTE]
>  The settings described here also apply to HIPAA interchanges.  
> 
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
  
1. Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, under **Interchange Settings** section, click **Local Host Settings**.  
  
3. Clear the **Route ACK to send pipeline on request-response receive port** to return the acknowledgment by a separate send port. Leave the property selected to return the acknowledgment on the send port associated with the two-way request-response receive port.  
  
4. To designate the range of transaction set control numbers used in an acknowledgment, enter values in the **ACK Control number (ST02)** fields. Enter a numeric value for the middle two fields, and an alphanumeric value (if desired) for the prefix and suffix fields. The middle fields are required and contain the minimum and maximum values for the control number; the prefix and suffix are optional. The maximum length for all three fields is nine characters.  
  
    To reset the current transaction set control number to the minimum value, click **Reset**. Check **Reset to lower limit when out of bound** to reset the control number to the lower limit once the maximum value has been exceeded.  
  
5. Select **Mask security/authorization/password information in context property** check box to enable masking of authorization/password security information (the ISA2 and ISA4 fields) in the context property to prevent information disclosure.  
  
   > [!NOTE]
   >  When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives messages, it promotes the ISA header into the context of the message. Without masking, the security information within the context would be available to anyone with administrative privileges. To mask this information, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] replaces each character of the information with a **#** character. This is a one-way process: the **#** characters cannot be converted to actual characters.  
  
6. In the **Inbound batch processing option** drop-down, do the following:  
  
   1.  Select the default option **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets.  
  
   2.  Select **Split Interchange as Transaction Sets - suspend Interchange on Error** to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document. BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
   3.  Select **Preserve Interchange - suspend Interchange on Error** to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.  
  
   4.  Select **Preserve Interchange - suspend Transaction Sets on Error** to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange. With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets, while continuing to process all other transaction set.  
  
       > [!NOTE]
       >  If you select **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**, the interchange, group, and transaction set segment properties (which determine how BizTalk Server will create the ISA, GS, and ST headers of an outgoing interchange) do not apply. The interchange, group, and transaction-set headers that exist in the interchange that is being preserved are retained when the send pipeline processes it for sending.  
  
### To configure local host – sender’s settings  
  
1.  For **Interchange control number (ISA13)**, enter a range of values for the interchange control number to be used by BizTalk Server in generating an outgoing interchange. Enter a numeric value with a minimum of 1 and a maximum of 999999999. This is a mandatory field.  
  
     To reset the control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
2.  For **Group control number (GS06)**, enter the range of numbers that BizTalk Server should use for the group control number. Enter a numeric value with a minimum of one character and a maximum of nine characters. This is a required field.  
  
     To reset the group control number to the minimum value specified, click the **Reset** button. Check **Reset to lower limit when out of bound** to automatically reset to the minimum value if the maximum value is exceeded.  
  
3.  For **Transaction Set Control number (ST02)**, click **Apply new ID** and then enter a range of numeric values for the required middle fields, and alphanumeric values for the optional prefix and suffix. The maximum length of all four fields is nine characters.  
  
     To reset the current transaction set control number to the minimum value, click **Reset**. Select **Reset to lower limit when out of bound** to reset the control number to the minimum value if the maximum value has been exceeded.  
  
4.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md)