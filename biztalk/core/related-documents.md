---
title: "Related Documents | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "queries [BAM], document references"
  - "definition files [BAM], related documents"
  - "Query Builder [BAM portal], viewing details"
  - "document references [BAM]"
  - "Query Builder [BAM portal], document references"
  - "queries [BAM], viewing details"
ms.assetid: 9c5f2175-fe7c-40ec-910d-1ac5c8142045
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Related Documents
The Related Documents area of the query results detail displays a list of documents that are reference documents that relate to the activity. The documents can be of any type, including a CAD image, a .WAV file, or a purchase order. For example, a Purchase Order activity will typically have a Purchase Order as a base document type. The list will contain a link to the purchase order.  
  
## Adding document references  
 The list of related documents is generated in one of two ways:  
  
- When you develop your tracking profile you include a Document Reference URL node in the activity tree and then map it from a source containing a reference pointer to the physical document.  
  
- Your integration developer programmatically populates the list by calling your custom application.  
  
  Defining the document reference using either of these methods adds a row in the \<activityname\>_References table with the document location.  
  
  If neither of these tasks has been performed, the **Related Document** area is blank.  
  
## See Also  
 [Tracking Profile Editor](../core/tracking-profile-editor.md)