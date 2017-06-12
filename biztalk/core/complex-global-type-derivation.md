---
title: "Complex Global Type Derivation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbf429d0-64f4-4c43-a5f7-e8af050803b9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Complex Global Type Derivation
There are two types of inheritance in XSD: extension and restriction. BizTalk Editor provides access to this XSD functionality by using the following two **Record** node properties:  
  
-   **Base Data Type**. This property provides the list of all global complex types and simple types available for use as a base data type. The complex global types can be in the same schema or in any imported schema.  
  
-   **Derived By**. This property is used to choose between deriving by extension or by restriction. This property is automatically set to **Extension** when you set the **Base Data Type** property to any type in the list. If you set this property to **(Default)**, any type in the **Base Data Type** property is removed, disabling inheritance for the node.  
  
> [!NOTE]
>  The **Content Type** property is also set automatically to **ComplexContent** when derivation by extension or restriction is being used.  
  
 This section explains complex type derivation by using the extension and restriction mechanisms in greater detail.  
  
## In This Section  
  
-   [Complex Type Derivation Using the Extension Mechanism](../core/complex-type-derivation-using-the-extension-mechanism.md)  
  
-   [Complex Type Derivation Using the Restriction Mechanism](../core/complex-type-derivation-using-the-restriction-mechanism.md)