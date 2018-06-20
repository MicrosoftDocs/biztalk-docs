---
title: "Invalid address length | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8e16eb6-e77e-4361-ac91-0730004c4433
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid address length
## Details  

|                 |                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------|
|  Product Name   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| Product Version |                 [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                  |
|    Event ID     |                                              0                                              |
|  Event Source   |                                              0                                              |
|    Component    |                                              0                                              |
|  Symbolic Name  |                                              0                                              |
|  Message Text   | Invalid address length; specified address length is {0} characters, limit is {1} characters |

## Explanation  
 You provided an address that exceeds the maximum length of 255 characters for a WCF transport. This is a limitation imposed by BizTalk Server, not by WCF.  

## User Action  
 Use the following procedure to configure a valid address.  

#### To configure a valid address  

1. Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.  

2. In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.  

9. In the **Address (URI)** text box, ensure the address does not exceed the maximum length of 255 characters.
