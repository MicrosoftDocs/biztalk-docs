---
title: "Configuring Fallback Identifiers (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cb5b32c-96ec-4192-9a10-6668a2cb1195
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Identifiers (X12)
In the fallback agreement, you must set the X12 authorization and security properties in order to verify that the interchange is not being received by unauthorized recipients.  
  
> [!NOTE]
>  The interchange processing properties described here apply also to HIPAA interchanges.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To set sender, receiver, and security properties  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.  
  
2. In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Identifiers**.  
  
3. Enter values for the **ISA1-2 (Authorization qualifier and information)**. Select the value for the **Authorization qualifier (ISA1)** from the associated drop-down list. If this value is other than **00**, for the **Value (ISA2)** text box, enter a minimum of one alphanumeric character and a maximum of 10. This is an optional field. If you do specify these values, make sure they match the ISA1 and ISA2 fields in a received interchange otherwise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.  
  
4. Enter values for the **ISA3-4 (Security qualifier and information)**. Select the value for the **Security qualifier (ISA3)** from the drop-down list. If this value is other than **00**, for the **Value (ISA4)** text box, enter a minimum of one alphanumeric value and a maximum of 10. This is an optional field. If these values do not match the ISA3 and ISA4 fields in a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.  
  
   > [!NOTE]
   >  The value **03 – Password (for backward compatibility)**, is included for backward compatibility with [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and will be removed in future versions.  
  
5. Enter the values for **ISA5-6 (Sender qualifier and identifier)**. Select a value for the qualifier from the **Sender Id Qualifier (ISA5)** drop-down list. For the identifier, in the **Value (ISA6)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.  
  
6. Enter the values for **ISA7-8 (Receiver qualifier and identifier)**. Select a value for the qualifier from the **Receiver Id Qualifier (ISA7)** drop-down list. For the identifier, in the **Value (ISA8)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.  
  
7. Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.  
  
## See Also  
 [Configuring X12 Fallback Agreement Properties for Interchange Processing](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)