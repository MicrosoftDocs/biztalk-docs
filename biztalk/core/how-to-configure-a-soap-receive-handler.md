---
title: "How to Configure a SOAP Receive Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [SOAP adapters], receive handlers"
  - "SOAP adapters, receive handlers"
  - "receive handlers, SOAP adapters"
ms.assetid: e1174381-f36c-4131-83b7-26bfa879802e
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a SOAP Receive Handler
You can configure the SOAP receive handler settings by using the BizTalk Server Administration Console. If you configure the adapter using the BizTalk Server Administration Console, the handler override properties do not need to be set in BizTalk Explorer.  
  
### To change global variables for the SOAP receive handler  
  
1. In the BizTalk Server Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2. In the expanded adapter list, click **SOAP**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.  
  
3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated, and then click **OK**.  
  
## See Also  
 [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md)   
 [Consuming Web Services](../core/consuming-web-services.md)