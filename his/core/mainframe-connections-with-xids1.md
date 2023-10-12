---
description: "Learn more about: Mainframe Connections with XIDs"
title: "Mainframe Connections with XIDs1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Mainframe Connections with XIDs
Node ID is the identifier used for exchange identifications (XIDs) with most mainframes. Check to make sure that the following items match; if they do not, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is not identifying itself in a way that the host can recognize.  
  
|Identifier used on mainframe|Identifier to configure<br /><br /> on Host Integration Server|  
|----------------------------------|------------------------------------------------------------|  
|**IDBLK** and **IDNUM** in the PU definition|The two parts of the **Local Node ID** (configured on the connection)|  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)
