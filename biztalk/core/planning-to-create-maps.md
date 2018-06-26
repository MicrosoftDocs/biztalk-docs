---
title: "Planning to Create Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps, planning"
ms.assetid: e86af976-b989-4e24-80d5-3a9a3ac4e443
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning to Create Maps
You use maps to convert input messages conforming to one schema into output messages conforming to a different schema. These conversions may be simple or quite complex, involving calculations and consolidation of information.  

 The following table lists some of the questions that you need to answer when you plan to create maps.  


|       Planning question        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Recommendation                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| What maps do I need to create? |                                                                                                                  Make a list of the business documents that you will process with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Such a list might include, for example, a purchase order, an invoice, a shipping confirmation, and so on. The list might also include more than one of each such business document, such as when the structure of a purchase order you receive from one trading partner is different than the structure of a purchase order you receive from another trading partner.<br /><br /> Go through the list and decide which of the documents need to be in a different format, or which documents are best handled by conversion to a common format.                                                                                                                   |
|     Where do I need maps?      |                                                                                                                                                                                                                                                                                                                                                                                            You can use maps in send ports, receive ports, and in orchestrations representing business processes. Consider where you want or need to convert documents.                                                                                                                                                                                                                                                                                                                                                                                            |
| Do I have old maps to convert? | Maps created in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 should migrate without modification. Allocate enough time to test the migrated maps. However, maps created in older versions of BizTalk may not necessarily open in BizTalk Server. **Note:**  Maps created in the versions prior to [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] may work accurately in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009. But, those maps may not open in BizTalk Server. <br /><br /> Maps containing **Scripting** functoids or custom functoids may require additional work. For more information, see [Migrating Functoids](../core/migrating-functoids.md). |

## See Also  
 [About Maps](../core/about-maps.md)   
 [Migrating Functoids](../core/migrating-functoids.md)