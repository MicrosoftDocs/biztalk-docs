---
title: "How to Configure a WCF-NetNamedPipe Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-NetNamedPipe adapters, global adapters"
  - "configuring [WCF-NetNamedPipe adapters], global adapters"
  - "send handlers, WCF-NetNamedPipe adapters"
  - "configuring [WCF-NetNamedPipe adapters], send handlers"
ms.assetid: 1f281649-d09f-44eb-8af5-1f83233fab60
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-NetNamedPipe Send Handler
Use the following procedure to configure a WCF-NetNamedPipe send handler.  

### To change global variables for a WCF-NetNamedPipe send handler  

1. In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.  

4. In the **General** tab, click **Properties**. On the **Send handler** tab, do the following:  


   |        Use this         |                                                                                                                                                                                                                                                                             To do this                                                                                                                                                                                                                                                                             |
   |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maximum connections** | Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool. This limits the number of connections that are cached for each unique remote endpoint. You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint. If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetNamedPipe send ports running under this send hander.<br /><br /> The default is 10. |


5. Click **OK**.  

## See Also  
 [Consuming WCF Services](../core/consuming-wcf-services.md)   
 [Configuring the WCF-NetNamedPipe Adapter](../core/configuring-the-wcf-netnamedpipe-adapter.md)