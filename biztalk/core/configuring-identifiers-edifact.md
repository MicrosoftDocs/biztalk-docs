---
title: "Configuring Identifiers (EDIFACT) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 097292f2-1aa5-42e4-aeee-c7d4cbdae17c
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Identifiers (EDIFACT)
In the partner agreement, you must set the recipient reference password, in order to verify that the interchange is not being received by unauthorized recipients.  
  
> [!IMPORTANT]
>  The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.  
> 
> - **DestinationPartyName** under **Additional Agreement Resolvers** section.  
> 
>   The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party. For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To set the sender, recipient, and recipient password  
  
1.  Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md). To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.  
  
2.  On a one-way agreement tab, under **Interchange Settings** section, click **Identifiers**.  
  
3.  In the **Sender (UNB2)** section, do the following:  
  
    1.  For **Identification (UNB2.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35. This is a required field.  
  
    2.  For **Code qualifier (UNB2.2)**, select a value from the drop-down list. This is an optional field.  
  
    3.  For **Reverse routing address (UNB2.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is an optional field.  
  
4.  In the **Recipient (UNB3)** section, do the following:  
  
    1.  For **Identification (UNB3.1)**, enter an alphanumeric value with a minimum of one and a maximum of 35. This is a required field.  
  
    2.  For **Code qualifier (UNB3.2)**, select a value from the drop-down list. This is an optional field.  
  
    3.  For **Reverse routing address (UNB3.3)**, enter an alphanumeric value with a minimum of one character and a maximum of 14 characters. This is an optional field.  
  
    4.  If required, in the **Recipient reference password (UNB6)** section, enter values for the recipient reference password. For **Value (UNB6.1)**, enter an alphanumeric value with a minimum of one and a maximum of 14. For **Qualifier (UNB6.2)**, enter an alphanumeric value with a minimum of one character and a maximum of two characters. These are optional fields. If these values do not match the UNB6.1 and UNB6.2 fields in a received interchange, BizTalk Server will suspend the interchange.  
  
        > [!NOTE]
        >  The combination of **UNB6.1** and **UNB6.2** must be unique.  
  
        > [!NOTE]
        >  If you enter values for both UNB6.1 and UNB6.2, apply the changes and then blank out UNB6.1, the value in UNB6.2 will also be deleted and the field will be disabled.  
  
5.  In the **Additional Agreement Resolvers** section, for **DestinationPartyName** property, specify a value for the destination party. This value is also used to resolve outbound messages to an agreement. For more information see, [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
    > [!NOTE]
    >  You typically do not need to set the **DestinationPartyName** property. This property is available as part of the agreement properties to support upgrade scenarios. When upgrading from BizTalk Server 2006 R2 or BizTalk Server 2009, the **DestinationPartyName** property is set to the name of the party in BizTalk Server 2006 R2 or BizTalk Server 2009.  
  
6.  Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.  
  
    > [!IMPORTANT]
    >  If you click **OK** or **Apply** at this stage, you will get an error. That is because you still need to provide UNB2 and UNB3 values on the **Identifiers** tab for the other one-way agreement tab.  
  
## See Also  
 [Configuring Interchange Settings (EDIFACT)](../core/configuring-interchange-settings-edifact.md)