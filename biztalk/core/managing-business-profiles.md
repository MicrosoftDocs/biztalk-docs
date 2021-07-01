---
description: "Learn more about: Managing Business Profiles"
title: "Managing Business Profiles | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.resultsobject.businessprofile"
ms.assetid: cf98c5a4-71bb-440b-8172-717ed0eb8373
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Business Profiles
A business profile represents the business divisions within of an organization. Just like an organization can have various divisions, a party can have various [business profiles](trading-partners-and-business-profiles.md). 
  
A business profile represents a business division in an organization. Just like an organization can have many divisions (accounting, purchase, shipping, etc.), a party can have many business profiles, each representing a business division in an organization. Business profile properties contain the following information:  
  
-   General information such as business profile name  
  
-   Unique identities that can be associated with a business profile  
  
-   Encoding settings (for X12 and EDIFACT messages) and [protocol settings](../core/protocol-settings.md) (AS2) that defines how the business profile can send or receive messages from another party.  
  
This topic shows you how to create, view, edit, or delete a business profile.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## Create a business profile  
  
1.  In **BizTalk Server Administration**, expand the BizTalk group, and select **Parties**. 
2. In the **Parties and Business Profiles** pane, right-click a party, select **New**, and then select **Business Profile**.  
  
3.  In the **General** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Enter a business profile name.|  
    |**Description**|Enter a description for the business profile.|  
    |**Additional Properties – Name / Value**|Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want. **Note:**  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.|  
    |**Delete**|Select to delete the selected name-value pair.|  
  
4.  If required, add business identities for the business profiles. In the **Identities** tab, do the following:  
  
    > [!NOTE]
    >  Adding business identities at this stage is not mandatory. You can add the business identities later, as part of an agreement for the business profile. If you chose to add the business identifies now, they are available while creating an agreement for this business profile.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Select the empty cell, and from the drop-down grid, select an authenticating body that provides unique business identities to organizations. For example, **D-U-N-S (Dun & Bradstreet)**. Two business partners can opt for a mutually agreed business identity. For such scenarios, select **Mutually Defined** (for EDIFACT) or **Mutually Defined (X12)** (for X12).|  
    |**Qualifier**|Displays a predefined value based on the value you selected for **Name**.|  
    |**Value**|Enter a value for the business identity. You must make the following considerations while providing a value for business identities.<br /><br /> -   For a given party, you can have more than one business profile using the same combination of identity name and identity value. For example, you can have two business profiles for a party with **Name** as **Mutually Defined (X12)** and **Value** as **THEM**.<br />-   Across parties, you cannot have two business profiles using the same combination of identity name and identity value.|  
    |**Remove**|Select to remove the selected identity.|  
  
5.  If required, add the protocol settings for X12-encoded messages, EDIFACT-encoded messages, or the protocol settings for AS2 transport. See [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).  
  
6.  Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action validates the settings.  
  
## View or change a business profile  
  
1.  In **BizTalk Server Administration**, select **Parties**. 

2. In the **Parties and Business Profiles** pane, expand a party node to see the business profiles under it. Right-click a business profile you want to edit, and then select **Properties**.  
  
3.  In the **Profile Properties** dialog box, view or edit the profile. For information on the values that can be specified on the different pages in the **Profile Properties** dialog box, see [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).  
  
4.  Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action validates the settings.  

## Delete a business profile  
  
1.  In **BizTalk Server Administration**, select **Parties**.  
  
3.  In the **Parties and Business Profiles** pane, expand a party node to see the business profiles under it.  
  
4.  Right-click the business profile you want to delete, and then select **Delete**. 
  
5.  In the **Confirm delete business profile** dialog box, select **Yes** to delete the business profile.  


## See Also  
 [Managing EDI and AS2 Solutions](../core/managing-edi-and-as2-solutions.md)
