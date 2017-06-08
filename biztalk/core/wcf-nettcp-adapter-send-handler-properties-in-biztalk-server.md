---
title: "&lt;Host Name&gt; Properties Dialog Box, Send Handler Tab (WCF-NetTcp Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-nettcp.sendhandler.sendhandler"
helpviewer_keywords: 
  - "send handlers, WCF-NetTcp adapters"
  - "WCF-NetTcp adapters, send handlers"
ms.assetid: 7213db21-28be-4420-9f61-358e8620e3be
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Send Handler Tab (WCF-NetTcp Adapter Send Handler)
Use the **Send handler** tab to configure the send handler for the WCF-NetTcp adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Maximum connections**|Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool. This limits the number of connections that are cached for each unique remote endpoint. You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint. If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetTcp send ports running under this send hander.<br /><br /> The default is 10.|  
  
## See Also  
 [How to Configure a WCF-NetTcp Send Handler](../core/how-to-configure-a-wcf-nettcp-send-handler.md)