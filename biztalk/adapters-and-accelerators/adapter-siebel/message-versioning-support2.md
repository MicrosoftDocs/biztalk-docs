---
title: "Message Versioning Support2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message versioning, support for"
ms.assetid: 5b7b9202-9f45-450e-918f-b26a03711aab
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Versioning Support
The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations. The current version is http://Microsoft.LobServices.Siebel/2007/03. This means that for an Insert operation on an Account business object in the Siebel repository, the Insert operation surfaced by the adapter has the following:  
  
-   Node ID: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   Message action: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
  
-   Namespace: http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation  
  
> [!NOTE]
>  This feature does not provide backward compatibility with the earlier versions of the adapter.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)