---
title: "How to Configure a WCF-NetNamedPipe Receive Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [WCF-NetNamedPipe adapters], global variables"
  - "receive handlers, WCF-NetNamedPipe adapters"
  - "configuring [WCF-NetNamedPipe adapters], receive handlers"
  - "WCF-NetNamedPipe adapters, global variables"
ms.assetid: f7ab2228-1049-40f0-87f7-6330a8f40cfe
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-NetNamedPipe Receive Handler
Use the following procedure to configure a WCF-NetNamedPipe receive handler.  

### To change global variables for a WCF-NetNamedPipe receive handler  

1. In the BizTalk Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **WCF-NetNamedPipe**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  

4. In the **General** tab, click **Properties**. On the **Receive handler** tab, do the following:  


   |        Use this         |                                                                                                                         To do this                                                                                                                         |
   |-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maximum connections** | Specify the maximum number of connections that the listener can have waiting to be accepted by the application. When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.<br /><br /> The default is 10. |


5. Click **OK**.  

## See Also  
 [Publishing WCF Services](../core/publishing-wcf-services.md)   
 [Configuring the WCF-NetNamedPipe Adapter](../core/configuring-the-wcf-netnamedpipe-adapter.md)