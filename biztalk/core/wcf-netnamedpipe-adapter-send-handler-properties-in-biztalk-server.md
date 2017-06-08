---
title: "&lt;Host Name&gt; Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netnamedpipe.sendhandler.sendhandler"
helpviewer_keywords: 
  - "WCF-NetNamedPipe adapters, send handlers"
  - "send handlers, WCF-NetNamedPipe adapters"
ms.assetid: 0af57e28-4ec1-4ad8-9063-730132bda452
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Send Handler Tab (WCF-NetNamedPipe Adapter Send Handler)
Use the **Send handler** tab to configure the send handler for the WCF-NetNamedPipe adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Maximum connections**|Specify the maximum number of outbound connections for each endpoint that is cached in the connection pool. This limits the number of connections that are cached for each unique remote endpoint. You should set this value to be greater than the maximum number of connections that you expect to be cached for any unique remote endpoint. If the number of active outbound connections exceeds this maximum value, then the service may appear unresponsive to the WCF-NetNamedPipe send ports running under this send hander.<br /><br /> The default is 10.|  
  
## See Also  
 [How to Configure a WCF-NetNamedPipe Send Handler](../core/how-to-configure-a-wcf-netnamedpipe-send-handler.md)