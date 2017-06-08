---
title: "Type Reuse and Derivations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 240145ea-be41-40ce-8edd-3d4d00e2baec
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Type Reuse and Derivations
Within XML Schema definition (XSD) language, complex global types provide a mechanism for defining a structured data type that can be reused, and potentially redefined, at various locations within your schema. Perhaps the most classic example is an address structure that includes a name, street, city, state, and so on. Further, the name itself might be a structure that includes first, middle, and last name strings. If this complex structure is defined globally, you can use it in multiple locations within your schema, such as for both a shipping address and a billing address.  
  
 XSD also provides mechanisms for deriving one type from another. This includes both simple content types and complex content types. For example, a new type can be derived from a simple string type (such as, xs:string) such that the new type allows only a few particular strings as legal values. This type of derivation is known within XSD as derivation by restriction because the values allowed by the derived type are more restrictive than the values allowed by the base type.  
  
 An example of a derivation involving a complex type can be seen in the address type previously suggested. Suppose that the address type is designed to accommodate the addresses within a particular country/region, where the country/region itself is assumed in the address. To extend such an address type to handle international addresses, you can derive a new type from the original address type and then include additional information in the derived type, such as the country/region. This type of derivation is known within XSD as derivation by extension because the derived type has extended the base type.  
  
 This section describes type reuse and the ways in which you can use derivation to redefine types as they are reused.  
  
## In This Section  
  
-   [Complex Global Type Definition and Naming](../core/complex-global-type-definition-and-naming.md)  
  
-   [Ways to Use Complex Global Types](../core/ways-to-use-complex-global-types.md)  
  
-   [Simple Type Derivation](../core/simple-type-derivation.md)