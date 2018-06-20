---
title: "Managing Parties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.resultsobject.party"
helpviewer_keywords: 
  - "Administration Console [BizTalk Server], parties"
  - "managing [parties]"
  - "managing [parties], about managing parties"
  - "parties, managing"
ms.assetid: 96d2bcb3-1e38-4dad-a0d6-e5913ba531e7
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Parties
Using the **Parties** node, you can set up business partners (parties) or internal departments (business profiles) with which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions interact. For more information, see [Trading Partners](../core/trading-partners-and-business-profiles.md).  

You can create and configure a party using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. After you create a party in BizTalk Server, it is likely that you want to interact with that party using an orchestration. Parties interact with orchestrations through roles. For example, you might have a shipping role in your orchestration. The shipper would have one or more parties associated with it. When the orchestration needs to decide the least expensive shipping company to use to ship an item, it can compare the prices of the parties in the shipper role.  

 You must enlist a party to tie it to a specific role. Enlisting a party enables an orchestration to interact with the party. See [How to Enlist or Unenlist a Party for a Role](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md).

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

## Create or edit a party

1. Open **BizTalk Server Administration**.  Expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **Parties**, select **New**, and then select **Party**.  

2. On the **General** page, do the following:  


   |                                                Use this                                                 |                                                                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                                                                       |
   |---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                **Name**                                                 |                                                                                                                                                                                                                                                                  Enter a party name.                                                                                                                                                                                                                                                                  |
   | **Local BizTalk processes messages received by the party or supports sending messages from this party** | Select this checkbox to specify that the party represents the same trading partner that also hosts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. **Important:**  For a two-party TPM solution that uses out-of-the-box pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must select this check box for at least one party. **Note:**  If you clear this check box, some properties will be disabled while creating the agreements for this party. |
   |                                **Additional Properties – Name / Value**                                 |                                                                                                                                                Enter a name-value pair to store any information about the party. You can add as many name-value pairs as you want. **Note**:  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.                                                                                                                                                 |
   |                                               **Delete**                                                |                                                                                                                                                                                                                                                    Select to delete the selected name-value pair.                                                                                                                                                                                                                                                     |


3. On the **Send Ports** page, do the following.  

   > [!NOTE]
   >  In BizTalk Server, the send port association is done at the agreement level. The **Send Ports** page available as part of the party properties is purely for backward compatibility. Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well. However, the reverse is not true. You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.  

   |       Use this        |                                      To do this                                       |
   |-----------------------|---------------------------------------------------------------------------------------|
   | **Send ports - Name** |          From the drop-down list, select a send port to bind to this party.           |
   | **Send ports - URI**  |                            Displays the send port address.                            |
   |      **Remove**       |                Select to remove the selected send port from the party.                |
   |    **Properties**     | Select to display the **Send Port Properties** dialog box for the selected send port. |


4. On the **Certificate** page, do the following:  


   |        Use this        |                                                                                                                                                 To do this                                                                                                                                                 |
   |------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **Browse**       |                                                Select to display the **Select Certificate** dialog box, where you select the signature certificate from the Local Machine or Other People certificate store to apply to messages transmitted to the party.                                                 |
   |    **Common Name**     |                                                                                                                            Displays a description of the selected certificate.                                                                                                                             |
   |     **Thumbprint**     | Displays the thumbprint of the private key certificate that is used for party resolution and signature verification. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F). |
   | **Remove certificate** |                                                                                                                                Select to remove the displayed certificate.                                                                                                                                 |


5. Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action will validate the settings  

### Update an existing party
After a party is enlisted to a role and the ports are bound, you can:  

- Edit the party's name and description  
- Edit the party's certificate  
- Specify whether the party is for the organization hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]

1. In **BizTalk Server Administration**, and select **Parties**.

2. In the **Parties and Business Profiles** pane, right-click the party you want to view or edit, and then select **Properties**.  

3. View or edit the properties. 

4. Select **Apply** to accept the properties, or select **OK** to complete the configuration setting. Either action validate the settings.  

## Delete a party
Delete the party using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  

> [!IMPORTANT]
>  You can only delete a party that is not enlisted in a role. Before you can delete a party, you must first un-enlist it from any of the roles where it is enlisted. See [How to Enlist or Unenlist a Party for a Role](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md). 

1. In **BizTalk Server Administration**, select **Parties**, right-click the party you want to delete, and then select **Delete**.  

2.  In the **Confirm delete party** dialog box, select **Yes** to delete the party.  

## Search for a party
If you have a large number of parties created, you can use the **Search** option to  display the parties that you want to see.  

1. In **BizTalk Server Administration**, select **Parties**.

2. In the **Parties and Business Profiles** pane, towards the top right corner, enter a search string in the **Search Party** text box, and select the search icon. You can also press ENTER to start the search.  

    You must consider the following points while using search:  

   - The search string is not case-sensitive

   - You can search for text within the name (sub-string search). For example, if you search for ‘ar’, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console displays the parties that either start with the search string (e.g. Artist) or the parties that have the search string in their name (e.g. Party1).  

   - The search operation is limited to party names.  

3. To clear the search results, select the red 'x' next to the search text box.  

## See Also  
 [Managing Role Links](../core/managing-role-links.md)   
 [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
 [Managing EDI and AS2 Solutions](../core/managing-edi-and-as2-solutions.md)