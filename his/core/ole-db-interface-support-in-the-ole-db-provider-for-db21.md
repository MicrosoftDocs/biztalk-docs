---
description: "Learn more about: OLE DB Interface Support in the OLE DB Provider for DB2"
title: "OLE DB Interface Support in the OLE DB Provider for DB21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3dac35d-f7c4-4e96-b1db-f105fa5a06fb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# OLE DB Interface Support in the OLE DB Provider for DB2
The following table summarizes the OLE DB version 2.0 interfaces that are supported by the current version of Microsoft OLE DB Provider for DB2.  
  
|Object|Interface|Support|  
|------------|---------------|-------------|  
|[Command Object](../core/command-object-ole-db-provider-for-db2-2.md)|**IAccessor**|Yes|  
||**IColumnsInfo**|Yes|  
||**IColumnsRowset**|Yes|  
||**ICommand**|Yes|  
||**ICommandPersist**|No|  
||**ICommandPrepare**|Yes|  
||**ICommandProperties**|Yes|  
||**ICommandText**|Yes|  
||**ICommandWithParameters**|Yes|  
||**IConvertType**|Yes|  
||**ISupportErrorInfo**|Yes|  
|[CustomErrorObject Object](../core/customerrorobject-object-ole-db-provider-for-db2-1.md)|**IErrorLookup**|Yes|  
||**ISQLErrorInfo**|Yes|  
|[DataSource Object](../core/datasource-object-ole-db-provider-for-db2-2.md)|**IDBAsynchStatus**|Yes|  
||**IConnectionPointContainer**|No|  
||**IDBCreateSession**|Yes|  
||**IDBDataSourceAdmin**|Yes|  
||**IDBInfo**|Yes|  
||**IDBInitialize**|Yes|  
||**IDBProperties**|Yes|  
||**IPersist**|Yes|  
||**IPersistFile**|Yes|  
||**ISupportErrorInfo**|Yes|  
|**Enumerator**|**IDBInitialize**|No|  
||**IDBProperties**|No|  
||**IParseDisplayName**|No|  
||**ISourcesRowset**|No|  
||**ISupportErrorInfo**|No|  
|[ErrorObject Object](../core/errorobject-object-ole-db-provider-for-db2-1.md)|**IErrorRecords**|Yes|  
|[ErrorRecord Object](../core/errorrecord-object-ole-db-provider-for-db2-1.md)|**IErrorInfo**|Yes|  
|**Index**|**IAccessor**|No|  
||**IColumnsInfo**|No|  
||**IConvertType**|No|  
||**IRowset**|No|  
||**IRowsetChange**|No|  
||**IRowsetFind**|No|  
||**IRowsetIdentity**|No|  
||**IRowsetIndex**|No|  
||**IRowsetInfo**|No|  
||**IRowsetLocate**|No|  
||**IRowsetRefresh**|No|  
||**IRowsetScroll**|No|  
||**IRowsetUpdate**|No|  
||**IRowsetView**|No|  
||**ISupportErrorInfo**|No|  
|**MultipleResults**|**IMultipleResults**|Yes (Stored Procedures)|  
||**ISupportErrorInfo**|No|  
|[Rowset Object](../core/rowset-object-ole-db-provider-for-db2-1.md)|**IAccessor**|Yes|  
||**IChapteredRowset**|No|  
||**IColumnsInfo**|Yes|  
||**IColumnsRowset**|Yes|  
||**IConnectionPointContainer**|No|  
||**IConvertType**|Yes|  
||**IDBAsynchStatus**|No|  
||**IRowset**|Yes|  
||**IRowsetChange**|Yes|  
||**IRowsetChapterMember**|No|  
||**IRowsetFind**|No|  
||**IRowsetIdentity**|No|  
||**IRowsetIndex**|No|  
||**IRowsetInfo**|Yes|  
||**IRowsetLocate**|No|  
||**IRowsetRefresh**|No|  
||**IRowsetScroll**|No|  
||**IRowsetUpdate**|Yes|  
||**IRowsetView**|No|  
||**ISupportErrorInfo**|Yes|  
|[Session Object](../core/session-object-ole-db-provider-for-db2-1.md)|**IAlterIndex**|No|  
||**IAlterTable**|No|  
||**IDBCreateCommand**|Yes|  
||**IDBSchemaRowset**|Yes|  
||**IGetDataSource**|Yes|  
||**IIndexDefinition**|No|  
||**IOpenRowset**|Yes|  
||**ISessionProperties**|Yes|  
||**ISupportErrorInfo**|Yes|  
||**ITableDefinition**|No|  
||**ITransaction**|Yes|  
||**ITransactionJoin**|No|  
||**ITransactionLocal**|Yes|  
||**ITransactionObject**|Yes|  
|[Transaction Object](../core/transaction-object-ole-db-provider-for-db2-1.md)|**IConnectionPointContainer**|No|  
||**ISupportErrorInfo**|Yes|  
||**ITransaction**|Yes|  
|**TransactionOptions**|**ISupportErrorInfo**|Yes|  
||**ITransactionOptions**|Yes|  
|**View**|**IAccessor**|No|  
||**IColumnsInfo**|No|  
||**ISupportErrorInfo**|No|  
||**IViewChapter**|No|  
||**IViewFilter**|No|  
||**IViewRowset**|No|  
||**IViewSort**|No|
