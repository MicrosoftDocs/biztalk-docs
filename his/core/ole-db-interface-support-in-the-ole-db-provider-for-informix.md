---
title: "OLE DB Interface Support in the OLE DB Provider for Informix | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcc30a34-7488-4013-b6d0-c692a352f107
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# OLE DB Interface Support in the OLE DB Provider for Informix
The following table summarizes the OLE DB version 2.8 interfaces that are supported by the current version of Microsoft OLE DB Provider for Informix.  
  
|Object|Interface|Support|  
|------------|---------------|-------------|  
|Command Object|**IAccessor**|Yes|  
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
|CustomErrorObject Object|**IErrorLookup**|Yes|  
||**ISQLErrorInfo**|Yes|  
|DataSource Object|**IDBAsynchStatus**|Yes|  
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
|ErrorObject Object|**IErrorRecords**|Yes|  
|ErrorRecord Object|**IErrorInfo**|Yes|  
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
|Rowset Object|**IAccessor**|Yes|  
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
|Session Object|**IAlterIndex**|No|  
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
|Transaction Object|**IConnectionPointContainer**|No|  
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