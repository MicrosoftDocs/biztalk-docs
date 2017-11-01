---
title: "Define Implementation Characteristics for the .NET Object Wizard Page (for HIP)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15383"
ms.assetid: 2e2c692e-5693-4ab9-b905-34b8f1806469
caps.latest.revision: 3
robots: noindex,nofollow
---
# Define Implementation Characteristics for the .NET Object Wizard Page (for HIP)
Use the **Define Implementation Characteristics for the .NET Object** wizard page to identify a .NET assembly implementing the interface defined in the Transaction Integrator metadata (TIM) file.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Defer implementation identification**|Select this option to identify the implementing assembly later through the object's **Properties** dialog.|  
|**Pick assembly**|Select this option to identify the implementing assembly now.|  
|**Path**|Type the full path name, including the .dll extension, to a .NET file, select a recently used file from the list, or click **Browse** and navigate to the file.|  
|**Class**|Select the class containing the methods to be called by HIP runtime for the request processing. The list dislays classes from the selected assembly that implement the interface defined in the .TIM file. The first class is selected in the list by default.|  
  
## See Also  
 [Completing the Object Wizard Page (for HIP)](../core/completing-the-object-wizard-page-for-hip.md)   
 [Object Wizard (for HIP)](../core/object-wizard-for-hip.md)