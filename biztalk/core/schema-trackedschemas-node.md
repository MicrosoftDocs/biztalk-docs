---
title: "Schema (TrackedSchemas Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schema node"
ms.assetid: a503aad6-07f8-4650-a214-4d2f6650cb80
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema (TrackedSchemas Node)
The Schema node of the TrackedSchemas node of a binding file describes a schema bound to a service that is exported with the binding file.  
  
## Nodes in the Schema node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribute|xs:string|Specifies the full name for the schema.|Not required|Default value: empty|  
|AssemblyQualifiedName|Attribute|xs:string|Specifies the qualified name for the assembly containing this schema.|Not required|Default value: empty|  
|AlwaysTrackAllProperties|Attribute|xs:boolean|Specifies whether to track all properties for the specified assembly.|Required|Default value: none<br /><br /> Set to **true** to track all properties, otherwise set to **false**.|  
|Description|Attribute|xs:string|Specifies a description for the schema.|Not required|Default value: empty|  
|[TrackedPropertyNames (Schema Node)](../core/trackedpropertynames-schema-node.md)|Record|ArrayOfString (ComplexType)|Container for the elements that specify the properties to be tracked.|Not required|Default value: none|