---
title: "Session Object (OLE DB Provider for Informix) | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a155b1b1-1ab0-43bd-9040-9ff41a39bc3d
caps.latest.revision: 2
author: MandiOhlinger
manager: anneta
ms.author: "v-mlynd"
---
# Session Object (OLE DB Provider for Informix)
The **Session** object is created by a **DataSource** object. The **Session** object is used to create one or more **Rowset** objects.  
  
 The following interfaces of the **Session** object are supported by the current version of Microsoft OLE DB Provider for Informix:  
  
-   **IDBCreateCommand**  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISessionProperties**  
  
-   **ISupportErrorInfo**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **ITransactionObject**  
  
 Consumers can get information about a data store without knowing its structure by using the **IDBSchemaRowset** methods. The methods on this interface can be used to retrieve advanced schema information. OLE DB Provider for Informix organizes each Informix database server in a set of schemas that contain tables for each schema. These schema rowsets are identified by globally unique identifiers (GUIDs).  
  
 The following schema rowset GUIDs are supported by OLE DB Provider for Informix:  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_INDEXES  
  
-   DBSCHEMA_PRIMARY_KEYS  
  
-   DBSCHEMA_PROCEDURES  
  
-   DBSCHEMA_PROCEDURE_PARAMETERS  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
-   DBSCHEMA_TABLES  
  
 The following table lists these GUIDs and the columns for which restrictions can be specified on the schema rowset when using OLE DB Provider for Informix. The number of restriction columns for each schema rowset are defined as constants prefixed with CRESTRICTIONS_ in the OLE DB header files. Restriction values are treated as literals rather than as search patterns. For example, the restriction value "A_C" matches "A_C" but not "ABC".  
  
|GUID|Number of restrictions|Restriction columns|  
|----------|----------------------------|-------------------------|  
|DBSCHEMA_COLUMNS|4|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|DBSCHEMA_INDEXES|4|TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|3|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURES|4|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE|  
|DBSCHEMA_PROCEDURE_PARAMETERS|4|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROVIDER_TYPES|2|DATA_TYPE BEST_MATCH|  
|DBSCHEMA_TABLES|4|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
 Note that the TYPE restriction on the DBSCHEMA_INDEXES GUID is not supported by OLE DB Provider for Informix.  
  
 The PROCEDURE_SCHEMA restriction on the DBSCHEMA_PROCEDURE GUID and the DBSCHEMA_PROCEDURE_PARAMETERS GUID is not supported when connecting to Informix servers.