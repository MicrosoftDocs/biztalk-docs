---
description: "Learn more about: Retrieving Schema Information"
title: "Retrieve Schema Information"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Retrieving Schema Information

## Overview
While an `Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader` is open, you can retrieve schema information about the current result set by using `MsDb2DataReader`.`Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.GetSchemaTable%2A`. `Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.GetSchemaTable%2A` returns a data table that is populated with rows and columns that contain the schema information for the current result set. The data table contains one row for each column of the result set. Each column of the schema table row maps to a property of the column returned in the result set, where the `ColumnName` is the name of the property and the value of the column is the value of the property.  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide2.md)   
