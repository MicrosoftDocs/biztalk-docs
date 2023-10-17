---
description: "Learn more about: DistributionList (DistributionListCollection Node)"
title: "DistributionList (DistributionListCollection Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DistributionList (DistributionListCollection Node)
The DistributionList node of a binding file contains specific information about a distribution list that is exported with the binding file. A distribution list is referred to as a send port group in the BizTalk Server Administrator.  
  
## Nodes in the DistributionList node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the distribution list.|Not required|Default value: empty|  
|[SendPorts](../core/sendports-distributionlist-node.md)|Record|ArrayOfSendPortRef (ComplexType)|Specifies the send port or send ports included in the distribution list.|Not required|Default value: none|  
|Filter|Element|xs:string|Specifies the name of the optional filter expression used on this distribution list.|Required|Default value: empty|  
|ApplicationName|Element|xs:string|Specifies the name of the application that the distribution list is associated with.|Required|Default value: empty|  
|Description|Element|xs:string|Specifies a description for the distribution list.|Required|Default value: empty|
