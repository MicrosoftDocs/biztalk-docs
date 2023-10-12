---
description: "Learn more about: TransportType (PrimaryTransport Node)"
title: "TransportType (PrimaryTransport Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TransportType (PrimaryTransport Node)
The TransportType node of the PrimaryTransport node of a binding file contains specific information about the adapter associated with a transport that is exported with the binding file.  
  
## Nodes in the TransportType node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the adapter associated with the transport.|Not required|Default value: empty|  
|Capabilities|Attribute|xs:int|Specifies the capabilities of the adapter associated with the transport.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.Capabilities](/dotnet/api/microsoft.biztalk.explorerom.capabilities) enumeration.|  
|ConfigurationClsid|Attribute|xs:string|Specifies the configuration GUID of the adapter associated with the transport.|Not required|Default value: empty|
