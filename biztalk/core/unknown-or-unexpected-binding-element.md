---
description: "Learn more about: Unknown or unexpected binding element"
title: "Unknown or unexpected binding element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unknown or unexpected binding element
## Details  

|      Field      |                                  Error Details                                     |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                       Unknown or unexpected binding element                        |

## Explanation  
 This error indicates the adapter cannot find the user defined binding element specified in the binding. This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.  

## User Action  
 Use the following procedure to verify binding elements are valid.  

#### To verify binding elements are valid  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the WCF **[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  

9. Ensure that the binding elements specified in the configuration are valid.
