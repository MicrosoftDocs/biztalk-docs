---
description: "Learn more about: Unable to import configuration"
title: "Unable to import configuration"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unable to import configuration
## Details  
  
|      Field      |                                  Error Details                                     |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                   Unable to import configuration from file "{0}"                   |
  
## Explanation  
 There could be multiple reasons for this error:  
  
-   The configuration file may contain invalid character in the given encoding.  
  
-   The root element may be missing.  
  
-   The data at the root level may be invalid.  
  
> [!NOTE]
>  This situation, and the user action, applies only to WCF-Custom and WCF-CustomIsolate adapters.  
  
## User Action  
 Use the following procedure to import a valid configuration file.  
  
#### To import a valid configuration file  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Import/Export** tab.  
  
9. Click **Import**. Import a valid and complete configuration file.  
  
   You can also verify the validity of the configuration file by opening it with the Service Configuration Editor **(Start > All Programs > Windows SDK)** (this step assumes you have the Windows SDK installed.) Open **svcConfigEditor.exe** and verify each property of the configuration file.
