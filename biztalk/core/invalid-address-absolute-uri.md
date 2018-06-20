---
title: "Invalid address (absolute uri) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5db292ad-9105-492d-a6c5-a7108159901a
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid address (absolute uri)
## Details  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |              Invalid address; "{0}" is not a well-formed absolute uri              |

## Explanation  
 This error event indicates that you did not provide an in-process WCF transport with a well-formed absolute address. For example, you cannot set the Address property of the in-process WCF transport to a relative address, such as /path/service.svc.  

## User Action  
 Change the address of the in-process WCF transport to a well-formed absolute address.  

1. Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.  

2. In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.  

3. Locate your application and then locate your transport.  

4. Right-click the transport name.  

5. Click **Properties**.  

6. In the port **Type** list, select the correct port.  

7. Click **Configure**.  

8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.  

9. In the **Address (URI)** text box. change the address. An example of a well-formed absolute address is http://localhost/path/service.svc
