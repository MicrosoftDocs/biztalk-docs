---
title: "Configuring Identifiers (X12) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 665698d1-c46c-4149-9715-381b4966dd92
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Identifiers (X12)
In the partner agreement, you must set the X12 authorization and security properties in order to verify that the interchange is not being received by unauthorized recipients.  
  
> [!NOTE]
>  The interchange processing properties described here apply also to HIPAA interchanges.  
> 
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **DestinationPartyName** under **Additional Agreement Resolvers** section.  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To set sender, receiver, and security properties  
  
1. Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2. On a one-way agreement tab, under **Interchange Settings** section, click **Identifiers**.  
  
3. Enter values for the **ISA1-2 (Authorization qualifier and information)**. Select the value for the **Authorization qualifier (ISA1)** from the associated drop-down list. If this value is other than **00**, for the **Value (ISA2)** text box, enter a minimum of one alphanumeric character and a maximum of 10. This is an optional field. If you do specify these values, make sure they match the ISA1 and ISA2 fields in a received interchange otherwise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.  
  
4. Enter values for the **ISA3-4 (Security qualifier and information)**. Select the value for the **Security qualifier (ISA3)** from the drop-down list. If this value is other than **00**, for the **Value (ISA4)** text box, enter a minimum of one alphanumeric value and a maximum of 10. This is an optional field. If these values do not match the ISA3 and ISA4 fields in a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.  
  
   > [!NOTE]
   >  The value **03 – Password (for backward compatibility)**, is included for backward compatibility with [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and will be removed in future versions.  
  
5. Enter the values for **ISA5-6 (Sender qualifier and identifier)**. Select a value for the qualifier from the **Sender Id Qualifier (ISA5)** drop-down list. For the identifier, in the **Value (ISA6)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.  
  
6. Enter the values for **ISA7-8 (Receiver qualifier and identifier)**. Select a value for the qualifier from the **Sender Id Qualifier (ISA7)** drop-down list. For the identifier, in the **Value (ISA8)** text box, enter a minimum of one alphanumeric character and a maximum of 15 characters.  
  
7. In the **Additional Agreement Resolvers** section, for **DestinationPartyName** property, specify a value for the destination party. This value is also used to resolve outbound messages to an agreement. For more information see, [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
   > [!NOTE]
   >  You typically do not need to set the **DestinationPartyName** property. This property is available as part of the agreement properties to support upgrade scenarios. When upgrading from BizTalk Server 2006 R2 or BizTalk Server 2009, the **DestinationPartyName** property is set to the name of the party in BizTalk Server 2006 R2 or BizTalk Server 2009.  
  
8. Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.  
  
   > [!IMPORTANT]
   >  If you click **OK** or **Apply** at this stage, you will get an error. That is because you still need to provide ISA5 to ISA8 values on the **Identifiers** tab for the other one-way agreement tab.  
  
## See Also  
 [Configuring Interchange Settings (X12)](../core/configuring-interchange-settings-x12.md)