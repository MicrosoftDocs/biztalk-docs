---
title: "Simple Type Derivation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d43932a0-039c-4211-82c0-087bae186145
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Simple Type Derivation
XML Schema definition (XSD) language provides several mechanisms for defining variations of simple types, based on derivations of existing simple types, as follows:  
  
- **Restriction**. Simple type derivation by using the restriction mechanism involves the introduction of restrictions to the possible values for that type. Examples are minimum and/or maximum values for numeric types, or a minimum and maximum length for string types.  
  
- **List**. Simple type derivation by using the list mechanism allows a single attribute or element value in an instance message to be defined as consisting of a list of space-separated values of a particular type.  
  
- **Union**. Simple type derivation by using the union mechanism allows a single attribute or element value in an instance message to be defined as a single value of one of several specified types.  
  
  This section describes these simple type derivations in more detail, including how to define these derivations by setting the appropriate node properties in the Properties window, as well as how the corresponding XSD is constructed.  
  
## In This Section  
  
-   [Simple Type Derivation Using the Restriction Mechanism](../core/simple-type-derivation-using-the-restriction-mechanism.md)  
  
-   [Simple Type Derivation Using the List Mechanism](../core/simple-type-derivation-using-the-list-mechanism.md)  
  
-   [Simple Type Derivation Using the Union Mechanism](../core/simple-type-derivation-using-the-union-mechanism.md)