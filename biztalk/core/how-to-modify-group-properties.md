---
title: "How to Modify Group Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying, groups"
  - "configuring, groups"
  - "groups, configuring"
  - "managing [groups], properties"
  - "groups, modifying"
  - "managing [groups], modifying"
  - "groups, properties"
ms.assetid: 59e0853d-81b0-43f9-85bf-099868e25fad
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify Group Properties
You can use this procedure to configure global properties for your BizTalk Server group so that you can select a signing certificate, modify the cache refresh interval, and determine how BizTalk Server will handle large messages. For more information about BizTalk Server group properties, see [BizTalk Groups](../core/biztalk-groups.md).  

## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Administrators group.  

### To configure BizTalk group properties  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **BizTalk Group**, and then click **Properties**.  

3. In the **Group Properties** dialog box, on the **General** tab, do the following:  


   |             Use this             |                                                                                                          To do this                                                                                                           |
   |----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |             **Name**             | Type the group name. The group name cannot exceed 128 characters in length. The name in this box appears next to the **Group** node in the console tree, along with the server name and the BizTalk Management database name. |
   |            **Server**            |                                                                      Displays the server on which the BizTalk Management database is physically stored.                                                                       |
   |           **Database**           |                                                            Displays the BizTalk Management database on which all configuration settings for this group are stored.                                                            |
   |       **SSO Server name**        |       Type the name of the Enterprise Single Sign-On (SSO) server that this computer will use to store and access adapter-specific information. This is the name of the SSO server used to connect to the SSO database.       |
   | **BizTalk Administrator Group**  |                                                  Displays the name of the administrators group that has rights to manage the BizTalk Server environment after installation.                                                   |
   |   **BizTalk Operators Group**    |                                Displays the name of the operators group that has rights to view configuration, run queries, and perform computer maintenance and basic application monitoring.                                |
   | **BizTalk Server B2B Operators** |                                                                                         Displays the name of the B2B operators group.                                                                                         |


4. On the **Databases** tab, do the following:  


   |   Use this    |                                                           To do this                                                            |
   |---------------|---------------------------------------------------------------------------------------------------------------------------------|
   | **Databases** | Displays the names of all databases in the application and the servers on which they reside, as specified during configuration. |


5. On the **Certificate** tab, do the following, and then click **OK**:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Common Name**|Displays a description of the selected certificate.|  
   |**Thumbprint**|Displays the thumbprint of the private key certificate that is used to digitally sign outbound messages from this group. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).|  
   |**Remove certificate**|Click to remove the displayed certificate.|  
   |**Browse**|Click to display the **Select Certificate** dialog box, where you select the signature certificate for the current user or personal store you want to use with the group.|  

## See Also  
 [Managing Groups](../core/managing-groups.md)   
 [BizTalk Groups](../core/biztalk-groups.md)   
 [How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md)   
 [How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md)   
 [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md)