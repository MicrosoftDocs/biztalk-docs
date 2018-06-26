---
title: "Unable to export service endpoint configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 795145fa-0ce4-498f-a82e-eb752a5f4764
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unable to export service endpoint configuration
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |              Unable to export service endpoint configuration to "{0}"              |
  
## Explanation  
 This error indicates the user may not have permission to write to the destination. Or some of the required properties were not correctly specified, such as Address (URI), and Binding Type.  
  
## User Action  
 Use the following procedure to configure the endpoint identity.  
  
#### To configure the endpoint identity  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the WCF **[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  
  
9. Ensure that writing to the destination folder is permitted.  
  
10. Check the **Behavior** tab and the **Endpoint Identity** settings in the **General** tab to ensure they are valid.  
  
    > [!NOTE]
    >  You must have write permissions to the destination folder. Contact the administrator of the machine to get these permissions.