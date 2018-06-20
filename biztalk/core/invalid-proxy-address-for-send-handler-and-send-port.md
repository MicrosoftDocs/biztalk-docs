---
title: "Invalid proxy address (for send handler and send port) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccedd23e-7d44-4419-b519-e04511e1f176
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invalid proxy address (for send handler and send port)
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                             Invalid proxy address: {0}                             |
  
## Explanation  
 You did not provide a WCF send handler or a WCF send port with a valid proxy address.  
  
## User Action  
 Use the following procedure to configure a proxy address.  
  
#### To configure a proxy address  
  
1. Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.  
  
2. In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.  
  
3. Locate your application and then locate your transport.  
  
4. Right-click the transport name.  
  
5. Click **Properties**.  
  
6. In the port **Type** list, select the correct port.  
  
7. Click **Configure**.  
  
8. In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Proxy** tab.  
  
9. Verify that the proxy address in the **Proxy settings** section is configured properly.  
  
   For additional information on send ports and send handlers, see the following resources:  
  
-   [How to Configure a WCF-WSHttp Send Port](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [How to Configure a WCF-BasicHttp Send Port](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [How to Configure a WCF-BasicHttp Send Handler](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [How to Configure a WCF-WSHttp Send Handler](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)