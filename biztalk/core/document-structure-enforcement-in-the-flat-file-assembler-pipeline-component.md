---
title: "Document Structure Enforcement in the Flat File Assembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, Flat File Assembler"
  - "Flat File Assembler [pipeline component], document structure"
ms.assetid: 3ac75706-1d4d-443a-a4bf-af8f79a6a092
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Structure Enforcement in the Flat File Assembler Pipeline Component
If document or envelope schemas are explicitly referenced in the Flat File Assembler, the Flat File Assembler ensures that only documents with the message type corresponding to referenced schemas are processed. All the other documents are not processed even though a schema may be deployed for them.  
  
> [!NOTE]
>  The envelope schema is taken from the first message only. The properties for the envelope are always taken from the first message.