---
title: "Ways to Use Complex Global Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddea1c7b-eb0e-4521-8576-0ea6f9460847
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ways to Use Complex Global Types
After you have converted a complex type to a global complex type, it becomes available for reuse in other locations within your schema. For more information about defining a complex type and then converting it to a global complex type, see [Complex Global Type Definition and Naming](../core/complex-global-type-definition-and-naming.md).  
  
 First, you insert a new **Record** node. Then you select the inserted node and set one of the following two node properties in the Properties window, each for a different effect:  
  
-   **Data Structure Type property**. If you want to use the complex global type without modifying it in any way, set this property to the type name you gave to the complex global type, which is available as a choice in the drop-down list. In the schema tree, the chosen global node structure will be graphically duplicated in the new location, and any subsequent changes to the node structure in any of its locations in the schema tree are automatically made to all locations that use that complex global type.  
  
-   **Base Data Type property**. If you want to use a variation on the complex global type, either extending it or restricting it in some way, set this property to the type name you gave to the complex global type, which is available as a choice in the drop-down list. When you set this property, the **Derived By** node property changes to **Extension** (and the **Content Type** property changes to **ComplexContent**), indicating that extending the complex global type is the default derivation type. You can change it to **Restriction** if your modifications are of that nature. Changes to the base complex global type from which you are deriving are automatically reflected in the derived type, but changes in the derived type are never reflected in the base type.  
  
> [!NOTE]
>  Setting either one of these properties automatically causes the other one to have any existing setting removed. Further, you will notice other automatic interactions between the related properties, such as setting the **Derived By** property to **(Default)** removes any existing setting from the **Base Data Type** property.  
  
> [!NOTE]
>  You can create a test schema and use different values for these properties, observing the changes in the XSD view.  
  
 This section describes using complex global types, both as is, and by extending and restricting them, as controlled by the settings of the properties described in this topic.  
  
## In This Section  
  
-   [Complex Global Type Re-use](../core/complex-global-type-re-use.md)  
  
-   [Complex Global Type Derivation](../core/complex-global-type-derivation.md)