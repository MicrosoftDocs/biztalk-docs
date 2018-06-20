---
title: "Transactions option &quot;Transactional&quot; and the error handling option &quot;Suspend request message on failure&quot; should not both be set to false | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transactions option &quot;Transactional&quot; and the error handling option &quot;Suspend request message on failure&quot; should not both be set to false
## Details  
  
|                 |                                                                                                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                |
| Product Version |                                                                            [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                            |
|    Event ID     |                                                                                                        0                                                                                                         |
|  Event Source   |                                                                                                        0                                                                                                         |
|    Component    |                                                                                                        0                                                                                                         |
|  Symbolic Name  |                                                                                                        0                                                                                                         |
|  Message Text   | The transactions option "Transactional" and the error handling option "Suspend request message on failure" should not both be set to false since message loss may occur. Please set one or both options to true. |
  
## Explanation  
 In the WCF-NetMsmq adapter, the options **Transactional** and **Suspend request message on failure** should not both be set to false (unchecked). Message loss may occur if the failed message submission does not roll back as a transaction, while the message is not suspended and stored in the Message Box.  
  
## User Action  
 Use the following procedure to verify adapter settings.  
  
#### To verify adapter settings  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.  
  
9. In the **Transactions** section, determine if **Transactional** is checked.  
  
10. Click the **Messages** tab.  
  
11. Determine if **Suspend request message on failure** is checked.  
  
    > [!NOTE]
    >  These steps only apply to receive locations.