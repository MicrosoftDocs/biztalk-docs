---
title: "Invalid address (relative uri needs slash (&quot;-&quot;)) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1376f924-f119-4ba8-9be1-eea7ba5f3eb6
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid address (relative uri needs slash (&quot;-&quot;))
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |         Invalid address; expecting relative uri starting with slash ("/")          |
  
## Explanation  
 You did not provide an isolated WCF receive location with a well-formed relative address. For example, http://localhost/svc will not work as a relative address. You cannot set the Address property of the isolated WCF receive location to a absolute address.  
  
## User Action  
 Use the following procedure to configure an address.  
  
#### To configure an address  
  
1. Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.  
  
9. In the **Address (URI)** text box, change the address. An example of a well-formed relative address is /path/service.svc.  
  
   For additional information on receive locations, see the following:  
  
-   [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [How to Configure a WCF-BasicHttp Receive Location](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)