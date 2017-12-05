---
title: "Mainframe Connections with XIDs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210560ee-5d8b-40b7-9cb2-592fe64e7cba
caps.latest.revision: 3
---
# Mainframe Connections with XIDs
Node ID is the identifier used for exchange identifications (XIDs) with most mainframes. Check to make sure that the following items match; if they do not, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is not identifying itself in a way that the host can recognize.  
  
|Identifier used on mainframe|Identifier to configure<br /><br /> on Host Integration Server|  
|----------------------------------|------------------------------------------------------------|  
|**IDBLK** and **IDNUM** in the PU definition|The two parts of the **Local Node ID** (configured on the connection)|  
  
## See Also  
 [Host Configuration](../core/host-configuration2.md)