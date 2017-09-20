---
title: "SendPorts (DistributionList Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SendPorts node [binding file]"
ms.assetid: 9cb645fa-cb9c-44eb-9f98-2fc507b2be67
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendPorts (DistributionList Node)
The SendPorts node of the DistributionList node of a binding file is the container node for the send port references in the distribution list.  
  
> [!NOTE]
>  A distribution list is referred to as a send port group in the BizTalk Administrator.  
  
## Nodes in the SendPorts node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[SendPortRef](../core/sendportref-sendports-node.md)|Record|SendPortRef (ComplexType)|Container node for a reference to a send port made by the distribution list.|Not required|Default value: none|