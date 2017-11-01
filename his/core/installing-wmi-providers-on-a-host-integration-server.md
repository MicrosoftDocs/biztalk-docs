---
title: "Installing WMI Providers on a Host Integration Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f5c2285-d96c-40a4-9bf4-bfffa8b4074f
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
---
# Installing WMI Providers on a Host Integration Server
Microsoft [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] provides several Windows Management Instrumentation (WMI) providers. The managed object format (MOF) files used by Host Integration Server are installed in the System directory below where [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] is installed. The default location for these files is in the following subdirectory:  
  
 C:\Program Files\Microsoft Host Integration Server 2013\System  
  
 To use or view these MOF files on other computers (a computer with the Administration client or end-user client, for example) to develop applications, these MOF files must be copied from the [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] computer. These MOF files document the WMI providers supplied with [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] and the class identifiers (CLSIDs), classes, properties, and methods supported by these providers.