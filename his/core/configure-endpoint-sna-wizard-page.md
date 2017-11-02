---
title: "Configure Endpoint SNA Wizard Page2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15205"
ms.assetid: 35065ddd-c1ac-4ce4-811d-767df9d8d958
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Configure Endpoint SNA Wizard Page
Use the **Configure SNA Endpoint** wizard page to set the local LU alias, the remote LU alias, and the APPC mode name for the host environment.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local LU alias**|Type the local LU alias. The alias can be a maximum of 256 alphanumeric characters. The drop-down list displays all the Local APPC LUs defined to the SNA Manager.|  
|**Remote LU alias**|Type the remote LU alias. The alias can be a maximum of 256 alphanumeric characters. The drop-down list displays all the remote APPC LUs defined to the SNA Manager.|  
|**Mode name**|Type the APPC mode used for the connection. You can obtain a list of configured modes from Host Integration Server **SNA Manager**. **Note:**  To use two-phase commit, the APPC mode must be Sync Level 2 capable.|  
  
## See Also  
 [Completing the New Remote Environment Wizard Page](../core/completing-the-new-remote-environment-wizard-page.md)   
 [New Remote Environment Wizard](../core/new-remote-environment-wizard.md)