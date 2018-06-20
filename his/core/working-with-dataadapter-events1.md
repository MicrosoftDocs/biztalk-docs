---
title: "Working with DataAdapter Events1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7db82781-c0df-4b02-b08c-f304ea70d094
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Working with DataAdapter Events
`MsDb2DataAdapter` exposes two events you can use to respond to changes made to data at the data source. The following table shows the `MsDb2DataAdapter` events.  
  
|Event|Description|  
|-----------|-----------------|  
|RowUpdating|An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.|  
|RowUpdated|An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.|  
  
 `RowUpdating` is raised before any update to a row from the dataset has been processed at the data source. `RowUpdated` is raised after any update to a row from the dataset has been processed at the data source. As a result, you can use `RowUpdating` to modify update behavior before it occurs, to provide additional handling when an update occurs, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on. `RowUpdated` is useful for responding to errors and exceptions that occur during the update. You can add error information, retry logic, and so on, to the dataset.  
  
## Arguments  
 The `MsDb2RowUpdatingEventArgs` and `MsDb2RowUpdatedEventArgs` arguments that are passed to the `RowUpdating` and `RowUpdated` events include the following:  
  
- A `Command` property that references the `Command` object that is used to perform the update.  
  
- A `Row` property that references the `DataRow` object containing the updated information.  
  
- A `StatementType` property for what type of update is being performed.  
  
- The `TableMapping`, if applicable.  
  
- The `Status` of the operation.  
  
  You can use the `Status` property to determine whether an error has occurred during the operation and, if you want, to control the actions against the current and resulting rows. When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.  
  
## Status Property Values  
 The following table shows the values to which you can set the `Status` property in order to control subsequent actions during the update.  
  
|Status|Description|  
|------------|-----------------|  
|Continue|Continue the update operation.|  
|ErrorsOccurred|Abort the update operation and throw an exception.|  
|SkipCurrentRow|Ignore the current row and continue the update operation.|  
|SkipAllRemainingRows|Abort the update operation, but do not throw an exception.|  
  
 Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown. You can control which exception is thrown by setting the `Errors` property to the desired exception. Using one of the other values for `Status` prevents an exception from being thrown.  
  
## See Also  
 [Working with the DataAdapter and the DataSet for a DB2 Database](../core/working-with-the-dataadapter-and-the-dataset-for-a-db2-database1.md)   
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)