---
title: "Index Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4bdd0f9-a9de-4194-9d4b-44460c23de8a
caps.latest.revision: 3
---
# Index Object (OLE DB Provider for AS-400 and VSAM)
An OLE DB index, also known as an **index rowset**, is a rowset built over an index in a data source. It is generally used in conjunction with a rowset built over a base table in the same data source. Each row of the index rowset contains a bookmark that points to a row in the base-table rowset. Thus, an OLE DB consumer can traverse the index rowset and use it to access rows in the base-table rowset.  
  
 Indexes are created using the index interfaces of the **Rowset** object. Index rowsets allow an application to read records efficiently by means of a key.  
  
 The following index interfaces of the **Rowset** object are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM when applied to AS/400 keyed physical files, AS/400 logical files, VSAM KSDS files with unique keys, and VSAM RRDS files with unique keys:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IConvertType**  
  
-   **IRowset**  
  
-   **IRowsetChange**  
  
-   **IRowsetFind**  
  
-   **IRowsetIdentity**  
  
-   **IRowsetIndex**  
  
-   **IRowsetInfo**  
  
-   **IRowsetLocate**  
  
-   **IRowsetRefresh**  
  
-   **IRowsetScroll**  
  
-   **IRowsetUpdate**  
  
-   **IRowsetView**  
  
-   **ISupportErrorInfo**  
  
 OLE DB Provider for AS/400 and VSAM supports integrated indexes using the **IRowsetIndex** interface based on the underlying rowset.