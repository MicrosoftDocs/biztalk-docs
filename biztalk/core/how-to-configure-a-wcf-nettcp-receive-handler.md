---
title: "How to Configure a WCF-NetTcp Receive Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-NetTcp adapters, global variables"
  - "receive handlers, WCF-NetTcp adapters"
  - "configuring [WCF-NetTcp adapters], global variables"
  - "configuring [WCF-NetTcp adapters], receive handlers"
ms.assetid: a4a283d1-21de-4d6b-9cb5-f2f9f823903b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-NetTcp Receive Handler
Use the following procedure to configure a WCF-NetTcp receive handler.  

### To change global variables for a WCF-NetTcp receive handler  

1. In the BizTalk Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **WCF-NetTcp**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  

4. In the **General** tab, click **Properties**, On the **Receive handler** tab, do the following.  


   |        Use this         |                                                                                                                         To do this                                                                                                                         |
   |-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maximum connections** | Specify the maximum number of connections that the listener can have waiting to be accepted by the application. When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.<br /><br /> The default is 10. |


5. Click **OK**.  

## See Also  
 [Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md)   
 [Publishing WCF Services](../core/publishing-wcf-services.md)