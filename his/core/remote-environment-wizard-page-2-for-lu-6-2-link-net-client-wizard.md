---
title: "Remote Environment Wizard Page 2 (for LU 6.2 Link) (.NET Client Wizard)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15479"
ms.assetid: 5d5b49a3-fda4-412a-9fcc-4e1cc796fec0
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Remote Environment Wizard Page 2 (for LU 6.2 Link) (.NET Client Wizard)
Use the **Remote Environment** wizard page to define the default values for the remote environment (RE).  
  
|Use this|To do this|  
|--------------|----------------|  
|**Transaction ID**|Type the transaction program (TP) name or the link mirror transaction ID of the remote environment. The name or ID can be a maximum of 4 alphabetic characters. The format of the name must conform to the IBM SNA Transaction Program Names convention. The default is **CSMI**.|  
|**Source TP name**|Type the name of the transaction program used by the method to locate a program to be executed. In the case of link models, the name identifies the mirror transaction identifier, which parses the distributed program link (DPL) header and identifies the link-to-program name. The name can be a maximum of 4 Unicode characters. The default is **MSTX**.|  
  
## See Also  
 [Library Properties](../core/library-properties.md)   
 [Completing the New .NET Client Library Wizard Page](../core/completing-the-new-net-client-library-wizard-page.md)   
 [New .NET Client Library Wizard](../core/new-net-client-library-wizard.md)