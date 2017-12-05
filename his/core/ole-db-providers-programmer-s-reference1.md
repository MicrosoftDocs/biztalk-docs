---
title: "OLE DB Providers Programmer&#39;s Reference1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eac13737-a62d-4c89-8934-a397ac209615
caps.latest.revision: 4
---
# OLE DB Providers Programmer&#39;s Reference
The OLE DB specification version 2.0 defines a number of objects and interfaces.  
  
 Microsoft OLE DB Provider for AS/400 and VSAM supports the OLE DB objects and interfaces appropriate for an OLE DB data provider accessing a non-SQL host file system.  
  
 Microsoft OLE DB Provider for DB2 supports the OLE DB objects and interfaces appropriate for an OLE DB data provider accessing an SQL database.  
  
 This section also provides a comparison of the objects and interfaces supported by OLE DB Provider for AS/400 and VSAM and OLE DB Provider for DB2.  
  
> [!NOTE]
>  Do not use double or real columns when specifying **UPDATE** or **DELETE** statements on the MsDb2DataAdapter. These rows will not be found and will throw the concurrency violation exception.  
  
## In This Section  
 [OLE DB Object Support in the OLE DB Provider for AS-400 and VSAM](../core/ole-db-object-support-in-the-ole-db-provider-for-as-400-and-vsam.md)  
  
 [OLE DB Object Support in the OLE DB Provider for DB2](../core/ole-db-object-support-in-the-ole-db-provider-for-db21.md)