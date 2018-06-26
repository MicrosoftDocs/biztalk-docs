---
title: "Cannot create binding | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbe1bd54-6031-4f90-a445-c1647b382a1a
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Cannot create binding
## Details  
  
|                 |                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                               |
| Product Version |                                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                           |
|    Event ID     |                                                                       0                                                                        |
|  Event Source   |                                                                       0                                                                        |
|    Component    |                                                                       0                                                                        |
|  Symbolic Name  |                                                                       0                                                                        |
|  Message Text   | Cannot create binding since binding type was not specified. Specify a binding type like "basicHttpBinding", "wsHttpBinding", or "customBinding |
  
## Explanation  
 You did not set the BindingType property in the code after configuring a WCF-Custom or a WCF-CustomIsolated transport. Or the problem could be in other code paths. You must have a value in the user interface for binding setting. Review your configuration and ensure that a binding type was chosen from the drop-down list in the receive location Properties area.  
  
## User Action  
 To resolve this error, review the code configuring the WCF-Custom or WCF-CustomIsolated transport. Ensure that the **BindingType** property in the XML data for the **TransportTypeData** property of the ITransportInfo interface is set properly.  
  
 Also, specify a binding type like **basicHttpBinding**, **wsHttpBinding**, or **customBinding**.  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  
  
9. Ensure that a value is specified in the **Binding Type** list.  
  
   For additional information on configuring binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)  
  
-   [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)