---
title: "Validating Instance Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Validate Instance command"
  - "testing, BizTalk Mapper"
  - "maps, testing"
  - "maps, validating"
  - "testing, maps"
  - "BizTalk Mapper, testing"
  - "BizTalk Mapper, validating"
ms.assetid: 19c3ca83-0abf-42ba-8e29-653ff12d5e20
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating Instance Data
During the process of testing a map, you may want to validate instance data against the source and destination schemas to verify that the instance data adheres to the schema structure. To validate an instance message against the source or destination schema, right-click the schema in the Solution Explorer, and then click **Validate Instance**.  
  
> [!IMPORTANT]
>  If you use custom data or constants in your output, you must verify that the data types of your source test data and target constant values are valid. When you validate a map, BizTalk Mapper does not check whether or not the instance data violates any data types defined by the schemas. This is done when you test the map or validate the instance data.  
  
 For more information about how to generate and validate instance data by using BizTalk Editor, see [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md) and [Instance Validation](../core/instance-validation.md). . The **Value** property of the node of a schema also affects how BizTalk generates instance data. For more information see [Schema Node Properties](../core/schema-node-properties.md).  
  
## See Also  
 [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md)   
 [How to Validate Schemas in Visual Studio](../core/how-to-validate-schemas-in-visual-studio.md)   
 [Map Property Reference](../core/map-property-reference.md)   
 [Testing Maps](../core/testing-maps.md)