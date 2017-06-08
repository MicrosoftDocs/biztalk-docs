---
title: "Functoids in Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoids"
  - "functoids, about functoids"
  - "functoid types, Record Count"
  - "functoid types, Looping"
  - "Looping functoids"
  - "functoids, categories"
  - "functoid types, Addition"
  - "Record Count functoids"
ms.assetid: 10ee8b62-cb20-4d26-9d86-b6564f30c297
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Functoids in Maps
BizTalk Mapper supports complex structural transformations from records and fields in the source schema to records and fields in the destination schema. Functoids perform calculations by using predefined formulas and specific values, called arguments. These calculations are executed based on the designated order of the records and fields.  
  
 By selecting a functoid from the Toolbox, dragging it to the grid page, and linking it to nodes in the source schema and destination schema, data can be added together, date or time information can be modified, data can be concatenated, or other operations can be performed. For example, the **Addition** functoid adds values and the **Record Count** functoid returns the total count of a looping record in an instance message. Categories of functoids that you can find in the Toolbox include: Advanced, Conversion, Cumulative, Database, Date/ Time, Logical, Mathematical, Scientific, and String.  
  
> [!NOTE]
>  All functoids are inline C# except for the Database functoids.  
  
> [!NOTE]
>  Destination schema nodes accept only one input from a functoid with the exception of the **Looping** functoid.  
  
 The topics in this section describe how to migrate functoids from previous versions of BizTalk Server, what functoids are, what they do, and how to use them.  
  
## In This Section  
  
-   [Functoid Categories](../core/functoid-categories.md)  
  
-   [Functoid Input Parameters](../core/functoid-input-parameters.md)  
  
-   [Basic Functoids](../core/basic-functoids.md)  
  
-   [Advanced Functoids](../core/advanced-functoids.md)  
  
-   [Cascading Functoids](../core/cascading-functoids.md)  
  
-   [Functoid Properties](../core/functoid-properties.md)  
  
-   [Migrating Functoids](../core/migrating-functoids.md)