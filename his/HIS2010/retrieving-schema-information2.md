---
title: "Retrieving Schema Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2945deb1-07a2-4b79-a652-fe19a13d31dc
caps.latest.revision: 4
---
# Retrieving Schema Information
While an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> is open, you can retrieve schema information about the current result set by using `MsDb2DataReader.`<xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.GetSchemaTable%2A>. <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.GetSchemaTable%2A> returns a data table that is populated with rows and columns that contain the schema information for the current result set. The data table contains one row for each column of the result set. Each column of the schema table row maps to a property of the column returned in the result set, where the `ColumnName` is the name of the property and the value of the column is the value of the property.  
  
## See Also  
 [Working with the Managed Provider for DB2](../HIS2010/working-with-the-managed-provider-for-db22.md)   
 [Managed Provider for DB2 Programmer's Guide](../HIS2010/managed-provider-for-db2-programmer-s-guide1.md)   
 [Managed Provider for DB2 Programmer's Reference &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/a50e991f-d651-40cb-a45c-d64fa132d251)