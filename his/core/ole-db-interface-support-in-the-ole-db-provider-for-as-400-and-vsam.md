---
title: "OLE DB Interface Support in the OLE DB Provider for AS-400 and VSAM | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da873887-1bb9-4ba2-9526-208c4d3cb50f
caps.latest.revision: 3
---
# OLE DB Interface Support in the OLE DB Provider for AS-400 and VSAM
The following table summarizes the OLE DB version 2.0 interfaces that are supported by the current version of Microsoft OLE DB Provider for AS/400 and VSAM.  
  
|Object|Interface|Support|  
|------------|---------------|-------------|  
|[Command Object](../core/command-object-ole-db-provider-for-as-400-and-vsam.md)|**IAccessor**|Yes|  
||**IColumnsInfo**|Yes|  
||**IColumnsRowset**|No|  
||**ICommand**|Yes|  
||**ICommandPersist**|No|  
||**ICommandPrepare**|No|  
||**ICommandProperties**|Yes|  
||**ICommandText**|Yes|  
||**ICommandWithParameters**|No|  
||**IConvertType**|Yes|  
||**ISupportErrorInfo**|Yes|  
|**CustomErrorObject**|**IErrorLookup**|No|  
||**ISQLErrorInfo**|No|  
|[DataSource Object](../core/datasource-object-ole-db-provider-for-as-400-and-vsam.md)|**IDBAsynchStatus**|No|  
||**IDBConnectionPointContainer**|No|  
||**IDBCreateSession**|Yes|  
||**IDBDataSourceAdmin**|No|  
||**IDBInfo**|No|  
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
|[ErrorObject Object](../core/errorobject-object-ole-db-provider-for-as-400-and-vsam.md)|**IErrorRecords**|Yes|  
|[ErrorRecord Object](../core/errorrecord-object-ole-db-provider-for-as-400-and-vsam.md)|**IErrorInfo**|Yes|  
|[Index Object](../core/index-object-ole-db-provider-for-as-400-and-vsam.md)|**IAccessor**|Yes|  
||**IColumnsInfo**|Yes|  
||**IConvertType**|Yes|  
||**IRowset**|Yes|  
||**IRowsetChange**|Yes|  
||**IRowsetFind**|Yes|  
||**IRowsetIdentity**|Yes|  
||**IRowsetIndex**|Yes|  
||**IRowsetInfo**|Yes|  
||**IRowsetLocate**|Yes|  
||**IRowsetRefresh**|Yes|  
||**IRowsetScroll**|Yes|  
||**IRowsetUpdate**|Yes|  
||**IRowsetView**|Yes|  
||**ISupportErrorInfo**|Yes|  
|**MultipleResults**|**IMultipleResults**|No|  
||**ISupportErrorInfo**|No|  
|[Rowset Object](../core/rowset-object-ole-db-provider-for-as-400-and-vsam.md)|**IAccessor**|Yes|  
||**IChapteredRowset**|Yes|  
||**IColumnsInfo**|Yes|  
||**IColumnsRowset**|No|  
||**IConnectionPointContainer**|No|  
||**IConvertType**|Yes|  
||**IDBAsynchStatus**|No|  
||**IRowset**|Yes|  
||**IRowsetChange**|Yes|  
||**IRowsetChapterMember**|No|  
||**IRowsetFind**|Yes|  
||**IRowsetIdentity**|Yes|  
||**IRowsetIndex**|Yes|  
||**IRowsetInfo**|Yes|  
||**IRowsetLocate**|Yes|  
||**IRowsetRefresh**|Yes|  
||**IRowsetScroll**|No|  
||**IRowsetUpdate**|Yes|  
||**IRowsetView**|Yes|  
||**ISupportErrorInfo**|Yes|  
|[Session Object](../core/session-object-ole-db-provider-for-as-400-and-vsam.md)|**IAlterIndex**|No|  
||**IAlterTable**|No|  
||**IDBCreateCommand**|Yes|  
||**IDBSchemaRowset**|Yes|  
||**IGetDataSource**|Yes|  
||**IIndexDefinition**|No|  
||**IOpenRowset**|Yes|  
||**ISessionProperties**|Yes|  
||**ISupportErrorInfo**|Yes|  
||**ITableDefinition**|No|  
||**ITransaction**|No|  
||**ITransactionJoin**|No|  
||**ITransactionLocal**|No|  
||**ITransactionObject**|No|  
|**Transaction**|**IConnectionPointContainer**|No|  
||**ISupportErrorInfo**|No|  
||**ITransaction**|No|  
|**TransactionOptions**|**ISupportErrorInfo**|No|  
||**ITransactionOptions**|No|  
|[View Object](../core/view-object-ole-db-provider-for-as-400-and-vsam.md)|**IAccessor**|Yes|  
||**IColumnsInfo**|Yes|  
||**ISupportErrorInfo**|Yes|  
||**IViewChapter**|Yes|  
||**IViewFilter**|Yes|  
||**IViewRowset**|Yes|  
||**IViewSort**|Yes|