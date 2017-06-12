---
title: "PeopleSoft Enterprise Requirements | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PeopleSoft Enterprise, requirements"
  - "send handlers, PeopleSoft requirements"
  - "CLASSPATH environment variable"
  - "custom component interface object"
  - "system requirements"
  - "GET_CI_INFO.pc"
ms.assetid: fabd808d-d9b6-43b0-a12a-727189f00a9d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PeopleSoft Enterprise Requirements
## Send Handler PeopleSoft Requirements  
 Microsoft BizTalk Adapter for PeopleSoft Enterprise contains a custom component interface (CI) and provides access to it through a Java API. A custom CI object, `GET_CI_INFO`, is deployed in the PeopleSoft system using PeopleSoft Tools to provide metadata information that is required by BizTalk Adapter for PeopleSoft Enterprise. For more information, see [Preparing to Use PeopleSoft Enterprise](../core/preparing-to-use-peoplesoft-enterprise.md).  
  
 Uploading the custom component interface is a one-time occurrence. This file, `GET_CI_INFO.pc`, installs with the product and must be installed before you can use the adapter to browse CIs. You must have access to the PeopleSoft Application Designer, but the Application Designer application does not have to be on the BizTalk Server computer. You use the Application Designer to upload the custom CI onto the PeopleSoft computer that you browse.  
  
 You must have access to the PeopleSoft computer because you must set the environment variable CLASSPATH (or set the information in the **Transport Properties** screen) to point to PeopleSoft's `PSJOA/psjoa.jar` file.  
  
## See Also  
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 [Planning and Architecture](../core/planning-and-architecture13.md)