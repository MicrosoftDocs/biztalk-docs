---
title: "Configuring Fallback Local Host Settings (EDIFACT-Interchange Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecf5abb-9c12-44b0-bc58-94cb138515c3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Local Host Settings (EDIFACT-Interchange Settings)
The local host settings govern how the EDI interchanges are processed. The settings on this page can be divided into two categories – receiver’s settings (for incoming interchanges) and sender’s settings (for outgoing interchanges). As part of the receiver’s settings, you can specify how the acknowledgement control number will be generated. As part of the sender’s settings, you can specify how the control numbers are generated for outgoing messages.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure local host – receiver’s settings  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.  
  
2. In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Local Host Settings**.  
  
3. In the **EDIFACT ACK** section, to designate the transaction set reference numbers to be used in an acknowledgment, enter a value for the prefix, a range of reference numbers, and suffix.  
  
    Click **Reset** to reset the current transaction set reference number to the lower limit. Select **Reset to lower limit when out of bound** to have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reset the reference number to the lower range value limit if the maximum limit is exceeded.  
  
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
 [Configuring EDIFACT Fallback Agreement Properties for Interchange Processing](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)