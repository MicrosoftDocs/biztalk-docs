---
title: "Endpoints Tab (SNA Local Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15317"
ms.assetid: 9b67934c-803a-41f9-8084-8ce957494524
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Endpoints Tab (SNA Local Environment Properties)
Use the **Endpoints** tab to view, add, and delete endpoints in the local environment definition.  
  
|Use this|To do this|  
|--------------|----------------|  
|**New transaction program name**|Type the transaction program (TP) name or the link mirror transaction ID of the local environment. The name or ID can be a maximum of 64 alphabetic characters. The format of the name must conform to the IBM SNA Transaction Program Names convention. The name or ID cannot be the same as that of an existing name or ID in the **Defined transaction programs names**.|  
|**Add**|Click to validate the transaction program (TP) name or the link mirror transaction ID you typed. If the TP name or the link mirror transaction ID is valid, it appears in **Defined transaction program names**.|  
|**Defined transaction programs names**|View the existing TP names or the link mirror transaction IDs for the local environment.|  
|**Remove**|Click to remove one or more TP names or link mirror transaction IDs selected from the **Defined transaction programs names** available for use in the local environment.|  
  
> [!CAUTION]
>  The properties of a local environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the local environment to function incorrectly.  
  
## See Also  
 [Local Environments Node](../core/local-environments-node.md)   
 [Local Environment Node](../core/local-environment-node.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)