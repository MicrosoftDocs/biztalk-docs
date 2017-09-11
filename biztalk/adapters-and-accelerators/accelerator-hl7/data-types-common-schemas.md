---
title: "Data Types Common Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.X schemas, data types"
  - "2.X schemas, common schemas"
  - "common schemas"
ms.assetid: 6fd30cd3-9c4f-4391-9c79-a4dff11f2a46
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Types Common Schemas
The **datatypes_*\<version>*.xsd** schema file (where *\<version>* is the HL7 version number) contains the definition of all the HL7 elementary and composite data types for the corresponding HL7 version. The segments_*\<version>*.xsd file uses this file to match the corresponding HL7 version. The DataStructures Access database table generates the DataTypes_*\<version>*.xsd schema file. The following example is an entry for the HL7 elementary data type **ST**:  
  
```  
<xsd:simpleType name="ST">  
  <xsd:restriction base="xsd:string" />   
</xsd:simpleType>  
```  
  
 This example defines **ST** as a **string**.  
  
## See Also  
 [HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Segments Common Schemas](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)   
 [Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)