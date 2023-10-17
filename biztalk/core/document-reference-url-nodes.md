---
description: "Learn more about: Document Reference URL Nodes"
title: "Document Reference URL Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Document Reference URL nodes [Tracking Profile Editor]"
  - "Tracking Profile Editor, node descriptions"
  - "definition files [BAM], related documents"
ms.assetid: 38c8ae50-ed56-451c-9549-db852d4770e5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Document Reference URL Nodes
Document Reference URL nodes exist in the activity definition file that the developer imports from the knowledge worker created observation model. Document Reference URL nodes contain references to a location that contains a document that is related to this activity. This can be any type of document, for example an activity that represents a purchase order approval work flow, the Document Reference URL might point to the underlying purchase order document.  
  
## Working with Document Reference URL nodes  
 The data source for the Document Reference URL is typically the **MessageRefURL** BizTalk Server system property. You can also use custom schemas that store URLs and map the property to the Document Reference URL from the custom schema.  
  
 Items to note about Document Reference URLs:  
  
-   You can add one or more Document Reference URLs, but each node must have unique name within the activity.  
  
-   The **MessageRefURL** property needed to populate a Document Reference URL node is only populated with a value in the case of WSS, FILE, and FTP transport adapters.  
  
-   While business end-users can view this reference in the BAM portal, the primary purpose of the reference URL is to allow custom user interface developers to gain access to associated document information so that they can present it to the end user.  For more information on viewing the document reference in the BAM portal, see [Related Documents](../core/related-documents.md).  
  
## See Also  
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)
