---
title: "Configuring Fallback Identifiers (EDIFACT) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2ce56c1-44f1-42dc-94e8-36e5ba664f53
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Identifiers (EDIFACT)
In the fallback agreement, you must set the recipient reference password, in order to verify that the interchange is not being received by unauthorized recipients.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To set the sender, recipient, recipient password  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.  
  
2. In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Identifiers**.  
  
3. In the **Sender (UNB2)** section, do the following:  
  
   1.  For **Identification (UNB2.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35. This is a required field.  
  
   2.  For **Code qualifier (UNB2.2)**, select a value from the drop-down list. This is an optional field.  
  
   3.  For **Reverse routing address (UNB2.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is an optional field.  
  
   4.  For **Application reference ID (UNB7)**, enter an alphanumeric value with a minimum of one character and a maximum of six characters. This is a required field.  
  
4. In the **Recipient (UNB3)** section, do the following:  
  
   1.  For **Identification (UNB3.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35. This is a required field.  
  
   2.  For **Code qualifier (UNB3.2)**, select a value from the drop-down list. This is an optional field.  
  
   3.  For **Reverse routing address (UNB3.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is an optional field.  
  
   4.  If required, in the **Recipient reference password (UNB6)** section, enter values for the recipient reference password. For **Value (UNB6.1)**, enter an alphanumeric value with a minimum of one and a maximum of 14. For **Qualifier (UNB6.2)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters. These are optional fields. If these values do not match the UNB6.1 and UNB6.2 fields in a received interchange, BizTalk Server will suspend the interchange.  
  
       > [!NOTE]
       >  The combination of **UNB6.1** and **UNB6.2** must be unique.  
  
       > [!NOTE]
       >  If you enter values for both UNB6.1 and UNB6.2, apply the changes and then blank out UNB6.1, the value in UNB6.2 will also be deleted and the field will be disabled.  
  
5. Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
## See Also  
 [Configuring EDIFACT Fallback Agreement Properties for Interchange Processing](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)