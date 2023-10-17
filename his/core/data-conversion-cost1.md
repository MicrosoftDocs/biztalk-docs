---
description: "Learn more about: Data Conversion Cost"
title: "Data Conversion Cost1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bffbc7c2-d1c4-477f-9f48-941142cfbddf
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Data Conversion Cost
The following list provides advice on selecting the data types that convert most efficiently between Automation and COBOL.  
  
-   If the source and destination data types are not strictly dictated, you can decrease the amount of CPU resource consumed by Transaction Integrator (TI) by appropriately selecting the data conversions that are performed (that is, selecting the source and destination data types wisely).  
  
-   The most efficient way to pass data is to select an Automation type of `VT_BYTE` and a COBOL data type of `PIC X` untranslated. There is no conversion performed and the data is copied as is.  
  
-   The Automation type `VT_BSTR` (a UNICODE character string) converts efficiently to COBOL `PIC X`. Be aware that a `BSTR` is not the same as a C character data type; it is a Visual Basic `String`.  
  
-   The most efficient numeric data type conversions are `VT_I2` (Visual Basic `Integer` or C `short`) to COBOL `PIC S9(4) COMP`, and `VT_I4` to `PIC S9(8) COMP`.  
  
-   If the data type you want is a COBOL packed decimal, the best choice for data conversion performance is one of the Automation integer data types. If fractional parts are required (that is, a COBOL picture like `PIC S9(5)V99 COMP-3`), the best choice for the Automation type is `VT_DECIMAL` (Decimal) or `VT_CY` (Currency).  
  
-   When the COBOL data type is zoned decimal (that is, a COBOL picture similar to `PIC S9(7)V99 DISPLAY`), the same considerations as for packed decimal apply. It is slightly more work to convert Automation data types to and from zoned decimal than it is to perform the conversions to packed decimal. If the data is used in calculations on the mainframe system, it is more efficient to use packed decimal instead of zoned decimal.  
  
-   Converting floating point data types (Automation types `VT_R4` and `VT_R8`) is, in most cases, the most expensive. Converting `VT_R4` to a COBOL `COMP-1`, or `VT_R8` to a COBOL `COMP-2` (a COBOL floating point number) data type is the most efficient conversion involving floating-point numbers.  
  
## See Also  
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)
