---
description: "Learn more about: DistributionListRef (Port Node)"
title: "DistributionListRef (Port Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DistributionListRef (Port Node)
The DistributionListRef node of the Port node of a binding file contains information about a distribution list that is referenced by a service.  
  
> [!NOTE]
>  Distribution lists are referred to as send port groups in the BizTalk Server Administration Console.  
  
## Nodes in the DistributionListRef node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of a distribution list that is referenced by a service.|Not required|Default value: empty|
