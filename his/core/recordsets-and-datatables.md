---
title: "Recordsets and Datatables1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bce4a959-5f8c-4e50-a572-07e863cf3f47
caps.latest.revision: 3
---
# Recordsets and Datatables
A recordset is an Automation object that is a fixed-size, bounded, or unbounded table that contains simple rows of host data declarations (data types). A datatable is a .NET object that is identical to a recordset in every regard, except that you cannot use the **NewRecordset** function with datatables. After you have a recordset or datatable object, you can call methods on that object to gain access to its rows.  
  
 A recordset or datatable is implemented on top of row sets by Remote Data Service (RDS), which is a part of Microsoft Data Access Components (MDAC) version 2.5. You can use the **RDSServer.DataFactory** object to create a recordset or datatable and use ActiveX® Data Objects (ADO) to update or read the recordset.  
  
 A recordset or datatable provides a means of presenting and manipulating tabular data. Currently, recordsets cannot be nested, cannot contain arrays, and cannot contain user-defined types (UDTs).  
  
 Support for recordsets and databales enables TI to support what is effectively an array of a structure (or a record, in COBOL terminology) as well as a structure. A structure is represented as a fixed-size recordset or datatable where each column in the row contains a single data element. To deal with mainframe programming issues, TI classifies recordsets and datatables as fixed-size, bounded, or unbounded, in reference to the number of rows contained in the recordset or datatable.  
  
> [!IMPORTANT]
>  The OS/400 distributed program calls (DPC) programming model supports only fixed size recordsets and datatables. The programming model does not support unbounded recordsets and datatables, nor does it support the use of the OCCURS DEPENDING ON clause, or variably-sized recordsets and datatables.  
  
 For fixed-size, bounded, and unbounded TI recordsets and datatables, the layout of all rows in a particular recordset is the same and is defined at design time by using TI Project. If a recordset or datatable is an output or return value from the mainframe, TI run-time environment uses the **RDSServer.DataFactory** object to create a recordset or datatable and ADO to fill the recordset or datatable with the rows of data returned from the mainframe program.  
  
 Such a recordset is a disconnected recordset with a cursor type of adOpenForwardOnly. To scan the recordset requires calling **MoveFirst** and **MoveNext** to move through the rows. The recordset can be updated in place, but because it is disconnected from the true data source (the data source manipulated by the mainframe program that returned the data), the updates are not propagated to the original data source.  
  
 **NewRecordset** is a function that is supplied automatically for all TI components. This function is called to create a disconnected recordset object that can be passed into a TI method call. **NewRecordset** is provided as a convenience for TI client applications; it is not required to pass a recordset to a TI component's methods. The function can be called only for input or input/output recordset objects. The TI run-time environment creates a recordset object when the parameter is an output recordset object.  
  
## In This Section