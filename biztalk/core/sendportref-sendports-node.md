---
title: "SendPortRef (SendPorts Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SendPortRef node [binding file]"
ms.assetid: 6c799b23-a9a4-4686-a04e-0450b4eef889
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendPortRef (SendPorts Node)
The SendPortRef node of the SendPorts node of a binding file specifies the name of a send port referenced by a distribution list.  
  
> [!NOTE]
>  A distribution list is referred to as a send port group in the BizTalk Administrator.  
  
## Nodes in the SendPortRef node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send port referenced by the distribution list.|Not required|Default value: empty|