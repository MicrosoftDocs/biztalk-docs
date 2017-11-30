---
title: "Service Entries1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34d03aa-a525-4dee-91d8-13aa36488e56
caps.latest.revision: 3
---
# Service Entries
Each instance of a component appears to the system as a unique service. These services must be created using the Service Control Manager (SCM). The SCM creates a registry entry for each service under **SYSTEM\CurrentControlSet\Services**. This key contains all of the service-specific information.  
  
 The top-level service key contains information that the SCM uses to control the service. This includes the type of service that this key represents, how it should be started, what sort of error handling should be used, the path to the executable image, and so on. All information in this key should be handled by the SCM. Each service key also contains two subkeys—the Linkage key and the Parameters key.  
  
 The Linkage key is used by the Network Control Panel Applet to store binding information. The Parameters key contains information that is relevant to [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Setup, such as the name of the DLL responsible for handling a link service. All information in this key should be handled by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Server Setup. The Parameters key contains another key, ExtraParameters, which is used for any IHV-specific information, including component-specific parameters and other information not required by the main SNA Server Setup program.