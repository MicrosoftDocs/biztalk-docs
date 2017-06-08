---
title: "Schema Generation in the Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, generating"
  - "writing, schemas"
ms.assetid: 43b69383-bae0-401b-9620-d4302db799b2
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Generation in the Adapter
A TIBCO Rendezvous system does not include a message types repository. All the message construction and parsing is buried at the Rendezvous application level. Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.  
  
## Writing Schemas  
 You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations. Schemas are very important for BizTalk Server development tools and for integration in Visual Studio. BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.  
  
## See Also  
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)