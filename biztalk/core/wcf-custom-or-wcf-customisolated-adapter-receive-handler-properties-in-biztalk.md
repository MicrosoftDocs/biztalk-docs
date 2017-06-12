---
title: "&lt;Host Name&gt; Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.handler.receive.extensions"
helpviewer_keywords: 
  - "bts09.adapters.wcf-custom.handler.receive.extensions"
ms.assetid: 2647fd12-92b5-4682-a4f7-b262bcef8a0a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler)
Use the **WCF Extensions** tab to configure the receive handler for the WCF-Custom or WCF-CustomIsolated adapter.  
  
> [!NOTE]
>  For all Send and Receive WCF-Custom and WCF-CustomIsolated handlers, the name of the binding extension element should always map to the same Binding Type. This is regardless of the host the handler is tied to.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Import**|Imports a WCF configuration file with WCF custom behavior extensions. Clicking this button opens the **Import WCF configuration** dialog box to browse and locate a WCF configuration file. Note that the file should be a valid WCF configuration file. For more information about WCF configuration schema, see “Windows Communication Foundation Configuration Schema” at [http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953).|  
|**Export**|Exports the WCF custom behavior extension to a WCF configuration file. Clicking this button opens the **Export WCF configuration** dialog box to browse and save the WCF configuration file.|  
|**Clear**|Clears the existing WCF custom behavior extension from the adapter handler properties.|  
  
## See Also  
 [How to Configure a WCF-Custom Receive Handler](../core/how-to-configure-a-wcf-custom-receive-handler.md)   
 [How to Configure a WCF-CustomIsolated Receive Handler](../core/how-to-configure-a-wcf-customisolated-receive-handler.md)