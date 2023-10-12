---
description: "Learn more about: Required property binding type not specified (R2)"
title: "Required property binding type not specified (R2)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Required property binding type not specified (R2)
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                    Required property Binding Type not specified                    |
  
## Explanation  
 You did not set the Binding Type property when configuring a WCF-Custom or a WCF-CustomIsolated transport.  
  
## User Action  
 Use the following procedure to configure the binding type property.  
  
#### To configure the binding type property  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF--[**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  
  
9. Specify a value in the **Binding Type** list.  
  
   For additional information on configuring binding, see the following resources:  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)
