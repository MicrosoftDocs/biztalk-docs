---
title: "Pre-Activation of the LU 6.2 Sessions1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30d57655-c8bd-48c3-bba6-063c157c8a24
caps.latest.revision: 3
---
# Pre-Activation of the LU 6.2 Sessions
Activating LU 6.2 sessions in advance will automatically prevent a short delay in establishing new LU 6.2 sessions as Transaction Integrator (TI) conversation allocation requests are made. In addition, pre-activating sessions keeps idle sessions active during the SESTIMEOUT period (approximately 20 seconds).  
  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] honors its APPC mode automatic activation limit setting for any APPC LU/LU partnership defined within the APPC mode when the connection is initially activated. Partnerships are defined in the **APPC-mode Partners** tab.  
  
 For more information about the `SesTimeout` registry parameter, search the Host Integration Server online Help.  
  
## See Also  
 [SNA Communication Tuning](../HIS2010/sna-communication-tuning1.md)