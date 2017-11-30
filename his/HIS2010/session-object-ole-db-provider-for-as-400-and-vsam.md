---
title: "Session Object (OLE DB Provider for AS-400 and VSAM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c741aa0-53eb-4ab8-8e20-c1196d37ffd7
caps.latest.revision: 3
---
# Session Object (OLE DB Provider for AS-400 and VSAM)
The **Session** object is created by a **DataSource** object. The **Session** object is used to create one or more **Rowset** objects.  
  
 The following interfaces of the **Session** object are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM:  
  
-   **IDBCreateCommand**  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISessionProperties**  
  
-   **ISupportErrorInfo**  
  
 Consumers can get information about a data store without knowing its structure by using the **IDBSchemaRowset** methods. The methods on this interface can be used to retrieve advanced schema information. OLE DB Provider for AS/400 and VSAM organizes this information into a set of schemas that contain tables for each schema. These schema rowsets are identified by globally unique identifiers (GUIDs).  
  
 The following schema rowset GUIDs are supported by OLE DB Provider for AS/400 and VSAM:  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_INDEXES  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
-   DBSCHEMA_TABLES  
  
 The following table lists these GUIDs and the columns for which restrictions can be specified on the schema rowset when using OLE DB Provider for AS/400 and VSAM. The number of restriction columns for each schema rowset are defined as constants prefixed with CRESTRICTIONS_ in the OLE DB header files. Restriction values are treated as literals rather than as search patterns. For example, the restriction value "A_C" matches "A_C" but not "ABC".  
  
|GUID|Number of restrictions|Restriction columns|  
|----------|----------------------------|-------------------------|  
|DBSCHEMA_COLUMNS|4|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|DBSCHEMA_INDEXES|5|TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TYPE TABLE_NAME|  
|DBSCHEMA_PROVIDER_TYPES|2|DATA_TYPE BEST_MATCH|  
|DBSCHEMA_TABLES|4|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
 The **IDBSchemaRowset** interface allows an application to pass at run time the target library of a partitioned data set (PDS), a dataset, or a member name when using the **IDBSchemaRowset:GetSchemas** function to retrieve the schema.  
  
 This following example illustrates using a target library to retrieve a table schema:  
  
```  
hr = pIDBSchemaRowset->GetRowset(  
        NULL,                        // punkOuter  
        DBSCHEMA_TABLES,             // schema IID  
         2L,                         // # of restrictions  
         rgRestrictions,             // array of restrictions  
         IID_IRowset,                // rowset interface  
         0L,                         // # of properties  
         NULL,                       // properties  
         (IUnknown**)&pIRowset);     // rowset pointer  
  
```  
  
 The variable *rgRestrictions* is an array containing two restriction values. The first array entry is VT_EMPTY and the second array entry is the target library name.