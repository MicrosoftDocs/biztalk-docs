---
title: "Error Handling Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 602be8a5-1f28-457d-8e12-ba06cff65491
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error Handling Errors
Information for diagnosing and resolving WCF Error Handling errors.  

## Error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false    

|                 |                                                                                                Details                                                                                                 |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                           |
| Product Version |                                                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                       |
|    Event ID     |                                                                                                   0                                                                                                    |
|  Event Source   |                                                                                                   0                                                                                                    |
|    Component    |                                                                                                   0                                                                                                    |
|  Symbolic Name  |                                                                                                   0                                                                                                    |
|  Message Text   | The error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false since message loss may occur. Please set one or both options to true |

## Explanation  
 In the WCF-NetMsmq adapter, the options **Disable location on failure** and **Suspend request message on failure** should not both be selected. Message loss may occur as the receive location continues to receive invalid messages, while these messages are not suspended and stored in the Message Box.  

## User Action  
 Use the following procedure to configure adapter settings.    

1. Open **BizTalk Server Administration**.  

2. In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Select **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Select **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, select the **Messages** tab.  

9. In the **Error Handling** section, ensure either **Disable location on failure** or **Suspend request message on failure** is checked.
