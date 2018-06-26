---
title: "Table-Driven Looping Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Table Looping functoids"
  - "Table Extractor functoids, configuring"
  - "Table Extractor functoids"
  - "Table Extractor functoids, adding to grid"
  - "Table Looping functoids, about Table Looping functoids"
  - "Table Looping functoids, configuring"
  - "Table Extractor functoids, about Table Extractor functoids"
  - "Table Looping functoids, adding to map"
ms.assetid: ecc24d9b-ebc0-4559-9746-58e3b00c02ab
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table-Driven Looping Configuration
Follow these steps to configure table-driven looping in your map:  
  
- **Add a Table Looping functoid to the map.** You need only one **Table Looping** functoid per table-driven looping instance. For example, if you are using table-driven looping to derive BillTo and ShipTo information, you need only one **Table Looping** functoid in your map. However, if you are using table-driven looping to derive BillTo and ShipTo information and StoreName and StoreAddress information, you might need two **Table Looping** functoids in your map.  
  
- **Add one more Table Extractor functoid to the displayed grid page.** Add as many **Table Extractor** functoids as you need for each **Table Looping** functoid. The number of **Table Extractor** functoids depends on the number of fields in the destination schema. For example, if you only have an **AddressCode** in your source schema and CompanyName, Address, City, State, PostalCode, and AttentionName in your destination schema, you need to add six **Table Extractor** functoids to the displayed grid page.  
  
- **Configure the Table Looping functoid with the appropriate inputs.** First, link the **Table Looping** functoid to the input instance record or element. Also link it to the structure in the output instance message. Next, configure the inputs by using the **Configure \<Functoid\> Functoid** dialog box. For more information about how to configure this property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md) . The list of inputs you enter must be comprehensive and complete because this is the data that you will use to configure the **Table Functoid Grid** property. The inputs must be defined as follows:  
  
  -   **First input.** The first input parameter is the link to the input instance message record or field. The **Table Looping** functoid loops once for each instance of the record or field.  
  
      > [!NOTE]
      >  This is a required input.  
  
  -   **Second input.** The second input parameter defines the number of columns in the looping grid. The grid may contain up to 228 columns.  
  
      > [!NOTE]
      >  This is a required input.  
  
  -   **Remaining inputs.** The remaining inputs for the **Table Looping** functoid consist of a list of all of the possible values that may appear in the **Table Functoid Grid**.  
  
      > [!NOTE]
      >  Labeling links is very helpful. Without labels, links appear in the **Table Functoid Grid** as fully specified paths.  
  
       For step-by-step instructions about how to configure inputs for the **Table Looping** functoid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). In particular, see steps 3 through 8.  
  
- **Configure the Table Functoid Grid property of the Table Looping functoid.** Use the **Table Functoid Grid** property to open the **Configure Table Looping Functoid** dialog box in which you configure the cells in the looping grid.  
  
   For step-by-step instructions about how to configure the looping grid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). In particular, see steps 9 and 10.  
  
- **Configure the Table Extractor functoids.** Use the **Input Parameters** property to configure the **Table Extractor** functoid inputs as follows:  
  
  - **First input.** The first input parameter to a **Table Extractor** functoid is the **Table Looping** functoid.  
  
  - **Second input.** The second input parameter specifies the column in the row from which to extract data.  
  
    For step-by-step instructions about how to configure the **Table Extractor** functoids associated with a **Table Looping** functoid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md). In particular, see steps 11 through 16.  
  
## See Also  
 [Table Looping Functoid](../core/table-looping-functoid.md)   
 [Table Extractor Functoid](../core/table-extractor-functoid.md)   
 [Table-Driven Looping Example](../core/table-driven-looping-example.md)   
 [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Index Functoid](../core/index-functoid.md)   
 [Iteration Functoid](../core/iteration-functoid.md)   
 [Looping Functoid](../core/looping-functoid.md)   
 [Record Count Functoid](../core/record-count-functoid.md)