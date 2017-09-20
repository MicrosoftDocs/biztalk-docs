---
title: "Message Versioning Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message versioning, support for"
ms.assetid: 650b966e-9fa6-4af8-a061-7852a892717a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Versioning Support
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports versioning by including a version string component in the message actions, namespaces, and node IDs surfaced for operations. The current version is http://Microsoft.LobServices.Sap/2007/03. This means that for an RFC named "RFC_SAMPLE", the RFC operation surfaced by the adapter has the following:  
  
-   Node ID: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE  
  
-   Message action: http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_SAMPLE  
  
-   Namespace: http://Microsoft.LobServices.Sap/2007/03/Rfc  
  
> [!NOTE]
>  This feature does not provide backward compatibility with the earlier versions of the adapter.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)