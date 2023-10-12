---
description: "Learn more about: WCF client must allow impersonation to use Single Sign-On"
title: "WCF client must allow impersonation to use Single Sign-On"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# WCF client must allow impersonation to use Single Sign-On
## Details  

|     Field       |                                    Error Details                                   |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |           The WCF client must allow impersonation to use Single Sign-On            |

## Explanation  
 Single Sign-On (SSO) is enabled in the receive location but the WCF client does not allow impersonation.  

## User Action  
 Ensure that the WCF client invoking the service allows impersonation.  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select **WCF-Custom** (or **WCF-CustomIsolate**).  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.  

9. In the **Behavior** section, click **ServiceAuthorization**. In the **Configuration** section, the property **ImpersonateCallerForAllOperations** should be set to **True**.  

10. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Other** tab.  

11. In the Credentials sections, select the option **Use Single Sign-On**.
