---
title: "Schema Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ea02c2a-ee00-4f44-9086-83d7ac4a8832
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Node

## Overview
In BizTalk Editor, the top of the schema hierarchy is always the **Schema** node, which cannot be renamed. The **Schema** node corresponds to the **schema** element in the XML Schema definition (XSD) language representation of the schema.  
  
> [!NOTE]
>  In BizTalk Editor, the **Schema** node is represented with the string \<Schema> in the schema tree view.  
  
 In general, the properties of the **Schema** node correspond to the attributes of the **schema** element in the XSD representation of the schema. For general information about node properties, see [Node Properties](../core/node-properties.md). For reference information about the properties of the **Schema** node, see the **Schema Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 When you create a new XML schema in BizTalk Editor, the **Schema** node and one **Root** node are created automatically.  
  
## XSD representation  
 The following example shows, in bold type, the lines in the XSD representation of the schema that correspond to the **\<Schema>** node in the tree view of the schema.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="Root">  
        <xs:complexType />  
    </xs:element>  
</xs:schema>  
```  
  
## See Also  
 [BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md)   
 [Node Properties](../core/node-properties.md)   
 [Set Node Properties](../core/how-to-set-node-properties.md)