---
title: "Operations on tables and views that contain large data types using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70f3b863-da3c-45b0-98f2-469a62286ebf
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on tables and views that contain large data types using the SQL adapter
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] provides supports for the following SQL Server large data types:  
  
- Varchar(Max)  
  
- Nvarchar(Max)  
  
- Varbinary(Max)  
  
  To read large data values from SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Select operation.  
  
  To write large data values to SQL Server, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the Set<column_name> operation, where <column_name> is the name of the column of type Varchar(Max), Nvarchar(Max) or Varbinary(Max). The Set<column_name> operation also allows adapter clients to write FILESTREAM data in SQL Server 2008.  
  
> [!NOTE]
>  The Set<column_name> operation is available only for those tables and views that contain columns with any of the three large data types mentioned earlier.  
  
 For detailed information about performing operations on tables and views in SQL Server that contain large data types, see [Operations on tables and views that contain large data types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).  
  
## See Also  
 [Connect to an SAP system using the adapter](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)