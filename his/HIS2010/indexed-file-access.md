---
title: "Indexed File Access | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9ae9da8-a604-4b42-90c5-ad75e1849db2
caps.latest.revision: 6
---
# Indexed File Access
The OLE DB Provider for AS/400 and VSAM provides both sequential and indexed file access. Sequential file access is provided for all supported file types on the [Platforms Supported by the OLE DB Provider for AS/400 and VSAM](../HIS2010/host-platforms.md).  
  
 Indexed file access is provided for the following host file types only:  
  
-   Mainframe Virtual Storage Access Method (VSAM) data sets.  
  
    -   Key-Sequenced Data Sets (KSDS) only when the keys are unique.  
  
    -   Fixed-length Relative Record Data Sets (RRDS) only when the keys are unique.  
  
    -   Variable-length Relative Record Data Sets (VRRDS) only when the keys are unique.  
  
-   Midrange i5/OS files.  
  
    -   Logical files.  
  
    -   Keyed physical files (externally described to the system).  
  
 OLE DB and ADO offer several interfaces that enable indexed file access.  
  
 The OLE DB Provider for AS/400 and VSAM supports integrated indexes based on the underlying rowset. OLE DB support for indexed file access using the OLE DB Provider for AS/400 and VSAM is available using the **IRowsetIndex**, **IViewFilter**, and **IViewRowset** interfaces.  
  
 For more information about indexes, see Chapter 10, "Index Rowsets" and Chapter 11, "Integrated Indexes" in the *OLE DB Programmer's Reference*. To obtain a list of available indexes in a target AS/400 library, a program can call the OLE DB **IDBSchemaRowset::GetRowset** function of the **Session** object requesting a query type of DBSCHEMA_INDEXES.  
  
 ADO support for indexed file access using the OLE DB Provider for AS/400 and VSAM is available using the **Find** method, **Filter** property, and **Sort** property on the ADO **Recordset** object. To obtain a list of available indexes in a target AS/400 library using ADO, a program can call the **OpenSchema** method on the **Connection** object specifying a *QueryType* of **adSchemaIndexes**.  
  
 By default, the OLE DB Provider for AS/400 and VSAM uses a server-based cursor. This means that all indexed file access is based on the cursor located over the host file and not a local computer copy of the host file. If you want to use the many client-based cursor service providers available with the Data Access Components (MDAC) 2.8, you must configure the provider to use a client-based cursor. For example, a client-based cursor is required when using Visual Studio® data-bound controls. However, using these controls, an application can access the host files for read-only purposes. If your application needs to access host files with an intent of both reading and writing, and you require indexed file access, your application should use the OLE DB Provider for AS/400 and VSAM server-based cursor.