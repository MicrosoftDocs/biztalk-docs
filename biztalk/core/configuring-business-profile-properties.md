---
title: "Configuring Business Profile Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.businessprofile.properties"
ms.assetid: d3c87777-9bcd-4482-bbb7-efea08cdeead
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Business Profile Properties
A business profile represents a business division in an organization. Just like an organization can have many divisions (accounting, purchase, shipping, etc.), a party can have many business profiles, each representing a business division in an organization. Business profile properties contain the following information:  

- General information such as business profile name  

- Unique identities that can be associated with a business profile  

- Encoding settings (for X12 and EDIFACT messages) and protocol settings (AS2) that defines how the business profile can send or receive messages from another party.  

  For more information about business profiles, see [Business Profiles](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf). For more information about encoding and transport protocol settings, see [Protocol Settings](../core/protocol-settings.md).  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

### To configure business profile properties  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node. In the **Parties and Business Profiles** pane, right-click a party, point to New, and then click **Business Profile**.  

2. In the **General** tab, on the **General** page, do the following:  


   |                 Use this                 |                                                                                                                       To do this                                                                                                                       |
   |------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                 **Name**                 |                                                                                                             Enter a business profile name.                                                                                                             |
   |             **Description**              |                                                                                                     Enter a description for the business profile.                                                                                                      |
   | **Additional Properties – Name / Value** | Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want. **Note:**  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only. |
   |                **Delete**                |                                                                                                     Click to delete the selected name-value pair.                                                                                                      |


3. If required, add business identities for the business profiles. In the **General** tab, on the **Identities** page, do the following:  

   > [!NOTE]
   >  Adding business identities at this stage is not mandatory. You can add the business identities later as well, as part of an agreement for the business profile. If you chose to add the business identifies now, they will be available while creating an agreement for this business profile.  

   |   Use this    |                                                                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                                                                       |
   |---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |   **Name**    |                                                                                        Click the empty cell, and from the drop-down grid, select an authenticating body that provides unique business identities to organizations. For example, **D-U-N-S (Dun & Bradstreet)**. Two business partners can opt for a mutually agreed business identity. For such scenarios, select **Mutually Defined** (for EDIFACT) or **Mutually Defined (X12)** (for X12).                                                                                         |
   | **Qualifier** |                                                                                                                                                                                                                                       Displays a predefined value based on the value you selected for **Name**.                                                                                                                                                                                                                                       |
   |   **Value**   | Enter a value for the business identity. You must make the following considerations while providing a value for business identities.<br /><br /> -   For a given party, you can have more than one business profile using the same combination of identity name and identity value. For example, you can have two business profiles for a party with **Name** as **Mutually Defined (X12)** and **Value** as **THEM**.<br />-   Across parties, you cannot have two business profiles using the same combination of identity name and identity value. |
   |  **Delete**   |                                                                                                                                                                                                                                                        Click to delete the selected identity.                                                                                                                                                                                                                                                         |


4. If required, add the protocol settings for X12-encoded messages.  

   1.  In the **Profile Properties** dialog box, from the top right corner, click **Add Protocol Settings**, point to **Encoding Settings**, and then click **X12**.  

   2.  A new tab gets added next to the **General** tab.  On the **Common** page of the newly added tab, in the **Protocol Settings Name** text box, enter a name to identify this set of encoding protocol settings. The name of the tab is also set to the value you specify in the text box.  

   3.  You can define the X12 properties either as part of a business profile or directly in the agreement. If you define the properties as part of the business profile, the same settings will be available to you when you create an agreement. Because the same properties can be set at two locations, this document provides instructions on how to set the properties only as part of the agreement. If you want to set the properties as part of the business profile, the table below provides links to relevant sections that contain information about setting the properties.  

       > [!NOTE]
       >  Inbound settings apply to all the messages received by a party. Outbound settings apply to all the messages sent by a party.  

       > [!NOTE]
       >  Even if you specify the protocol settings as part of the business profile, you can always overwrite the settings for a specific agreement.  

       |Setting|Description available at|  
       |-------------|------------------------------|  
       |**Inbound Settings > Interchange Settings > Validation**|[Configuring Validation (X12-Interchange Settings)](../core/configuring-validation-x12-interchange-settings.md)|  
       |**Inbound Settings > Interchange Settings > Local Host Settings**|[Configuring Local Host Settings (X12-Interchange Settings)](../core/configuring-local-host-settings-x12-interchange-settings.md) (Receiver’s Settings)|  
       |**Inbound Settings > Transaction Set Settings > Transaction Set List**|[Configuring Transaction Set List (X12)](../core/configuring-transaction-set-list-x12.md)|  
       |**Inbound Settings > Transaction Set Settings > Validation**|[Configuring Validation (X12-Transaction Set Settings)](../core/configuring-validation-x12-transaction-set-settings.md)|  
       |**Inbound Settings > Transaction Set Settings > Local Host Settings**|[Configuring Local Host Settings (X12-Transaction Set Settings)](../core/configuring-local-host-settings-x12-transaction-set-settings.md)|  
       |**Outbound Settings > Interchange Settings > Additional Identifiers**|[Configuring Identifiers (X12)](../core/configuring-identifiers-x12.md)|  
       |**Outbound Settings > Interchange Settings > Acknowledgements**|[Configuring Acknowledgements (X12)](../core/configuring-acknowledgements-x12.md)|  
       |**Outbound Settings > Interchange Settings > Envelopes**|[Configuring Envelopes (X12-Interchange Settings)](../core/configuring-envelopes-x12-interchange-settings.md)|  
       |**Outbound Settings > Interchange Settings > Charset and Separators**|[Configuring Charset and Separators (X12)](../core/configuring-charset-and-separators-x12.md)|  
       |**Outbound Settings > Interchange Settings > Control Numbers**|[Configuring Local Host Settings (X12-Interchange Settings)](../core/configuring-local-host-settings-x12-interchange-settings.md) (Sender’s Settings)|  
       |**Outbound Settings > Transaction Set Settings > Envelopes**|[Configuring Envelopes (X12-Transaction Set Settings)](../core/configuring-envelopes-x12-transaction-set-settings.md)|  

       > [!NOTE]
       >  You can have more than one X12 encoding protocol settings defined for a business profile.  

5. If required, add the protocol settings for EDIFACT-encoded messages.  

   1.  In the **Profile Properties** dialog box, from the top right corner, click **Add Protocol Settings**, point to **Encoding Settings**, and then click **EDIFACT**.  

   2.  A new tab gets added next to the **General** tab.  On the **Common** page of the newly added tab, in the **Protocol Settings Name** text box, enter a name to identify this set of encoding protocol settings. The name of the tab is also set to the value you specify in the text box.  

   3.  You can define the EDIFACT properties either as part of a business profile or directly in the agreement. If you define the properties as part of the business profile, the same settings will be available to you when you create an agreement. Because the same properties can be set at two locations, this document provides instructions on how to set the properties only as part of the agreement. If you want to set the properties as part of the business profile, the table below provides links to relevant sections that contain information about setting the properties.  

       > [!NOTE]
       >  Inbound settings apply to all the messages received by a party. Outbound settings apply to all the messages sent by a party.  

       > [!NOTE]
       >  Even if you specify the protocol settings as part of the business profile, you can always overwrite the settings for a specific agreement.  

       |Setting|Description available at|  
       |-------------|------------------------------|  
       |**Inbound Settings > Interchange Settings > Additional Identifiers**|[Configuring Identifiers (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
       |**Inbound Settings > Interchange Settings > Validation**|[Configuring Validation (EDIFACT-Interchange Settings)](../core/configuring-validation-edifact-interchange-settings.md)|  
       |**Inbound Settings > Interchange Settings > Local Host Settings**|[Configuring Local Host Settings (EDIFACT-Interchange Settings)](../core/configuring-local-host-settings-edifact-interchange-settings.md) (Receiver’s Settings)|  
       |**Inbound Settings > Transaction Set Settings > Transaction Set List**|[Configuring Transaction Set List (EDIFACT)](../core/configuring-transaction-set-list-edifact.md)|  
       |**Inbound Settings > Transaction Set Settings > Validation**|[Configuring Validation (EDIFACT-Transaction Set Settings)](../core/configuring-validation-edifact-transaction-set-settings.md)|  
       |**Inbound Settings > Transaction Set Settings > Local Host Settings**|[Configuring Local Host Settings (EDIFACT-Transaction Set Settings)](../core/configuring-local-host-settings-edifact-transaction-set-settings.md)|  
       |**Outbound Settings > Interchange Settings > Additional Identifiers**|[Configuring Identifiers (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
       |**Outbound Settings > Interchange Settings > Acknowledgements**|[Configuring Acknowledgements (EDIFACT)](../core/configuring-acknowledgements-edifact.md)|  
       |**Outbound Settings > Interchange Settings > Envelopes**|[Configuring Envelopes (EDIFACT-Interchange Settings)](../core/configuring-envelopes-edifact-interchange-settings.md)|  
       |**Outbound Settings > Interchange Settings > Charset and Separators**|[Configuring Charset and Separators (EDIFACT)](../core/configuring-charset-and-separators-edifact.md)|  
       |**Outbound Settings > Interchange Settings > Control Numbers**|[Configuring Local Host Settings (EDIFACT-Interchange Settings)](../core/configuring-local-host-settings-edifact-interchange-settings.md) (Sender’s Settings)|  
       |**Outbound Settings > Transaction Set Settings > Envelopes**|[Configuring Envelopes (EDIFACT-Transaction Set Settings)](../core/configuring-envelopes-edifact-transaction-set-settings.md)|  

       > [!NOTE]
       >  You can have more than one EDIFACT encoding protocol settings defined for a business profile.  

6. If required, add the protocol settings for AS2 transport.  

   1.  In the **Profile Properties** dialog box, from the top right corner, click **Add Protocol Settings**, point to **Transport Settings**, and then click **AS2**.  

   2.  A new tab gets added next to the **General** tab.  On the **Common** page of the newly added tab, in the **Protocol Settings Name** text box, enter a name to identify this set of transport protocol settings. The name of the tab is also set to the value you specify in the text box.  

   3.  You can define the AS2 properties either as part of a business profile or directly in the agreement. If you define the properties as part of the business profile, the same settings will be available to you when you create an agreement. Because the same properties can be set at two locations, this document provides instructions on how to set the properties only as part of the agreement. If you want to set the properties as part of the business profile, the table below provides links to relevant sections that contain information about setting the properties.  

       > [!NOTE]
       >  Inbound settings apply to all the messages received by a party. Outbound settings apply to all the messages sent by a party.  

       > [!NOTE]
       >  Even if you specify the protocol settings as part of the business profile, you can always overwrite the settings for a specific agreement.  

       |Setting|Description available at|  
       |-------------|------------------------------|  
       |**Inbound Settings > Validation**|[Configuring Validation (AS2)](../core/configuring-validation-as2.md)|  
       |**Inbound Settings > Local Host Settings > HTTP Settings for Messages**|[Configuring HTTP Settings for Messages](../core/configuring-http-settings-for-messages.md)|  
       |**Inbound Settings > Local Host Settings > Generated MDN Settings**|[Configuring Receiver MDN Settings](../core/configuring-receiver-mdn-settings.md)|  
       |**Inbound Settings > Local Host Settings > Message Tracking (NRR)**|[Configuring Receiver Message Tracking (NRR)](../core/configuring-receiver-message-tracking-nrr.md)|  
       |**Outbound Settings > Acknowledgements (MDNs)**|[Configuring Acknowledgements (MDNs) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)|  
       |**Outbound Settings > Local Host Settings > General**|[Configuring General Local Host Settings (AS2)](../core/configuring-general-local-host-settings-as2.md)|  
       |**Outbound Settings > Local Host Settings > HTTP Settings for MDN**|[Configuring HTTP Settings for MDNs](../core/configuring-http-settings-for-mdns.md)|  
       |**Outbound Settings > Local Host Settings > Message Tracking (NRR)**|[Configuring Sender Message Tracking (NRR)](../core/configuring-sender-message-tracking-nrr.md)|  
       |**Outbound Settings > Signature Certificate**|[Configuring Signature Certificates (AS2)](../core/configuring-signature-certificates-as2.md)|  

       > [!NOTE]
       >  You can have more than one AS2 transport protocol settings defined for a business profile.  

7. Click **Apply** to accept the properties, or click **OK** to complete the configuration setting. Either action will validate the settings.  

## See Also  
 [Configuring EDI Properties](../core/configuring-edi-properties.md)