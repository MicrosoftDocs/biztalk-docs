---
description: "Learn more about: Supported .NET Aggregate Data Types"
title: "Supported .NET Aggregate Data Types1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Supported .NET Aggregate Data Types
**Datatable**  
 A .NET Framework object that is the equivalent of a fixed or unbounded table that contains simple types in COBOL or Report Program Generator (RPG) data declarations. After you have a **DataTable** object, you can call methods on that object to gain access to its rows. Datatables supported by TI have disconnected, client-side cursors. For more information, see [Recordsets and Datatables](../core/recordsets-and-datatables1.md).  
  
 **Structures**  
 A user-defined value type. Like a class, structures can contain constructors, constants, fields, methods, properties, indexers, operators, and nested types. Unlike classes, however, structures do not support inheritance.  
  
 The distributed program call (DPC) programming model for the IBM System i supports:  
  
- Only single-level .NET structures.  
  
- Arrays of .NET structures.  
  
  The DPC programming model for the IBM System i does not support:  
  
- Nesting of structures.  
  
- Arrays within structures.  
  
- Variable sized structures in which the last parameter is a string.  
  
  **Array**  
  A set of sequentially indexed elements that have the same intrinsic data type. Transaction Integrator (TI) supports an array of any of the .NET data types in this topic. Each element of an array has a unique identifying index number. Changes made to one element of an array do not affect the other elements. TI supports multidimensional arrays. However, only the outermost array of a multidimensional array can vary in size; all the other arrays must be fixed in size.  
  
## See Also  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)
