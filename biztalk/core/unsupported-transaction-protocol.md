---
title: "Unsupported transaction protocol | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11fb2497-9971-4e85-b21a-161734f071e0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unsupported transaction protocol
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                       Unsupported transaction protocol: {0}                        |
  
## Explanation  
 This error occurs when the transaction protocol property of a receive location or send port is set to an invalid value.  
  
## User Action  
 To resolve this error, do one or more of the following:  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.  
  
9. In the **Transactions** section, choose the **Enable transactions** option.  
  
10. In the **Transactions protocol** drop-down list, choose either **OleTransactions** or **WSAtomicTransactions**.  
  
    These steps only apply to the following transport types:  
  
-   Custom  
  
-   CustomIsolated  
  
-   NetNamedPipe  
  
-   NetTcp  
  
-   WShttp