---
title: "ReceiveLocationTransportType (ReceiveLocation Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReceiveLocationTransportType node [binding file]"
ms.assetid: 375076c3-d5e6-4c25-b054-b452e29717e0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ReceiveLocationTransportType (ReceiveLocation Node)
The ReceiveLocationTransportType node of the ReceiveLocation node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.  
  
## Nodes in the ReceiveLocationTransportType node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the adapter associated with the transport.|Not required|Default value: empty|  
|Capabilities|Attribute|xs:int|Specifies the capabilities of the adapter associated with the transport.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) enumeration.|  
|ConfigurationClsid|Attribute|xs:string|Specifies the configuration GUID of the adapter associated with the transport.|Not required|Default value: empty|