---
description: "Learn more about: Mainframe Connections with XIDs"
title: "Mainframe Connections with XIDs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0b16406-3098-4e95-8b2f-d075dc579319
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Mainframe Connections with XIDs
Node ID is the identifier used for exchange identifications (XIDs) with most mainframes. Check to make sure that the following items match; if they do not, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is not identifying itself in a way that the host can recognize.  
  
|Identifier used on mainframe|Identifier to configure<br /><br /> on Host Integration Server|  
|----------------------------------|------------------------------------------------------------|  
|**IDBLK** and **IDNUM** in the PU definition|The two parts of the **Local Node ID** (configured on the connection)|  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)
