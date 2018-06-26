---
title: "Install, schemas, and limitations TIBCO Rendezvous adapter | Microsoft Docs"
description: Install, schema generation, and limitations of the BizTalk Adapter for TIBCO Rendezvous in BizTalk Server
ms.custom: ""
ms.date: "10/23/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6404e7e-f671-4c57-a222-0bbe7cbc334f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install, schemas, and limitations of the TIBCO Rendezvous adapter

## Install and setup

[Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) includes the steps to install the enterprise adapters, and also includes key information to know before you install the adapter, and after you install the adapter. 

## Generate schemas
A TIBCO Rendezvous system does not include a message types repository. All the message construction and parsing is buried at the Rendezvous application level. Because of this limitation, adapter cannot provide schema-generation capabilities.  
  
You must write a schema, and use **Add Existing Item** in Visual Studio to import it for use in orchestrations. Schemas are very important for BizTalk Server development tools and for integration in Visual Studio. BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.  

## Limitations

- Field name uniqueness is not guaranteed. If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.  
  
- Field ordering/sorting is not provided.  
  
- According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used. BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.  
  
- Secure connection to daemons is not supported.  
  
- Custom data types are not supported.  
  
- Certified Messaging is not supported on the transmit side.  
- 
  ## Next step

[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)  