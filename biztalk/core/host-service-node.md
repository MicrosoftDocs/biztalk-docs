---
description: "Learn more about: Host (Service Node)"
title: "Host (Service Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Host node [binding file]"
ms.assetid: 597522db-0336-43b1-b464-d17cffbf25be
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Host (Service Node)
The Host node of the Service node of a binding file describes the host associated with the service that is exported with the binding file.  
  
## Nodes in the Host node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the host.|Not required|Default value: empty|  
|NTGroupName|Attribute|xs:string|Specifies the Windows NT Group name associated with the host.|Not required|Default value: empty|  
|Type|Attribute|xs:int|Specifies the host type as in process or isolated.|Required|Default value: none<br /><br /> Possible values are described in the [Microsoft.BizTalk.ExplorerOM.HostType](/previous-versions/) enumeration.|  
|Trusted|Attribute|xs:boolean|Specifies whether the BizTalk host can be trusted to collect authentication information.|Required|Default value: none<br /><br /> Set to **true** if the host is trusted, otherwise set to **false**.|