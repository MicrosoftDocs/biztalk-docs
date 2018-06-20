---
title: "Unable to create service behavior configuration element from XML configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6732e5d2-bb4b-48ec-af59-467eede80f36
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unable to create service behavior configuration element from XML configuration
## Details  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |  Unable to create service behavior configuration element from XML configuration.   |

## Explanation  
 This error indicates the adapter did not load the service behavior configuration. This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.  

## User Action  
 Use the following procedure to configure the service behavior.  

#### To configure the service behavior  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.  

9. In the **Behavior** section, check the **ServiceBehavior** configuration.
