---
title: "Tabular Data Definition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8af7848f-fabf-4f3d-8653-84c13bd16a4d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Tabular Data Definition
In many cases, the input or output data that Transaction Integrator (TI) handles might be in tabular or array format. TI allows you to define this type of data as one of the following formats:  
  
- Recordset. A recordset provides a means of presenting and manipulating tabular data in a Microsoft ActiveX® Data Objects (ADO) environment. A recordset contains all of the ADO information to make it manageable by any ADO application. A recordset is the primary object used for retrieving and modifying tabular data by using ADO. A recordset object represents a set of records in a table. Recordsets allow TI to support what is effectively an array of a structure (or table in COBOL terminology); it even can support the special case of a structure that is a recordset containing only one row. Each column in the row can contain only a single data element. Recordsets cannot be nested or contain arrays.  
  
- User-defined type (UDT). Unlike recordsets, which must contain all of the formatting necessary to expose them to ADO applications, a UDT is just raw data and can therefore be faster than recordsets. A UDT can contain an ordinary (fixed-size) array. It can also contain a dynamic array. You can combine variables of several different types to create UDTs. UDTs are useful when you want to create a single variable that records several related pieces of information.  
  
- Array. In the COM/COM+ and .NET environments, arrays are SAFEARRAYs that contain information about their bounds and contain the data for the array elements. SAFEARRAYs are mapped to fixed-size arrays on the host computer. SAFEARRAYs have a variable size and require custom information to be marshaled to and from fixed-size arrays on the host computer.  
  
  Arrays are created on the mainframe computer during the import process when a simple data type has one or more OCCURS clauses. The OCCURS clause can represent a fixed or variable-length table. Although it is possible in COBOL to have nested OCCURS DEPENDING clauses, only the OCCURS DEPENDING length specifier for the outermost table dimension is supported by TI. The TI Designer ignores nested length specifiers.  
  
> [!NOTE]
>  A UDT and recordset that have the same fields look the same in COBOL.  
  
## See Also  
 [Transaction Integrator Basic Functions](../core/transaction-integrator-basic-functions1.md)