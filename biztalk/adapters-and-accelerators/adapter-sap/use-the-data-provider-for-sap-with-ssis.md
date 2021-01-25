---
description: "Learn more about: Use the Data Provider for SAP with SSIS"
title: "Use the Data Provider for SAP with SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for SAP, using with SSIS"
  - "SSIS, Data Provider for SAP"
ms.assetid: e8c50cc1-ac25-4993-9aee-7fd88268d65d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use the Data Provider for SAP with SSIS
You can use the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] along with SQL Server Integration Service (SSIS) to import data from an SAP system into SQL Server database tables, flat files, or other compatible destination types. You can create an SSIS package that can be executed to import data from an SAP system.  
  
 You must use the SQL Server Import and Export wizard to import data into the SQL Server database. You must provide a query to specify data to be imported. You can specify a query using the SELECT statement or the EXECQUERY statement. The query must confirm to the semantics supported by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md). For more information about the grammar for an EXECQUERY statement for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for an EXECQUERY Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).  
  
 You can start the SQL Server Import Export wizard either from the SQL Server Management Studio or from an Integration Service project in Visual Studio. This section provides instructions on running the wizard from both the Management Studio and Visual Studio interfaces.  
  
## In This Section  
  
-   [Import SAP Data Using SQL Server Management Studio](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-sql-server-management-studio.md)  
  
-   [Import SAP Data Using Visual Studio](../../adapters-and-accelerators/adapter-sap/import-sap-data-using-visual-studio.md)  
  
## See Also  
 [Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)
