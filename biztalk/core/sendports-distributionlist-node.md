---
description: "Learn more about: SendPorts (DistributionList Node)"
title: "SendPorts (DistributionList Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
