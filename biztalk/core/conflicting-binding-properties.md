---
title: "Conflicting binding properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b08c317e-a617-464b-9ee4-007fb41d99b2
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Conflicting binding properties
## Details  
  
|                 |                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                    |
| Product Version |                                               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                |
|    Event ID     |                                                                            0                                                                            |
|  Event Source   |                                                                            0                                                                            |
|    Component    |                                                                            0                                                                            |
|  Symbolic Name  |                                                                            0                                                                            |
|  Message Text   | Conflicting binding properties: MsmqAuthenticationMode={0} and MsmqProtectionLevel={1} is invalid. Change one of the properties to resolve the conflict |
  
## Explanation  
 The MSMQ protection level property of a WCF-NetMsmq transport was set to **Sign** or **EncryptAndSign** for the None MSMQ authentication mode.  
  
## User Action  
 Change the MSMQ protection level or the MSMQ authentication mode property to be consistent with the MSMQ protection level property.  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF-NetMsmq Transport Properties** dialog box, click the **Security** tab.  
  
9. Check the values in the MSMQ **authentication mode** list and the **MSMQ protection level** list.  
  
   For further information, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  
  
-   [How to Configure a WCF-NetMsmq Send Port](../core/how-to-configure-a-wcf-netmsmq-send-port.md)  
  
-   [How to Configure a WCF-NetMsmq Receive Location](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)