---
title: "Execute Stored Procedures in SQL Server using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 245626a7-f546-4aca-90df-c0579139a872
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Execute Stored Procedures in SQL Server using the SQL adapter
The Transact-SQL and CLR stored procedures in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] under the **Procedures** node while using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. The operation names exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] are the same as the name of the stored procedure in SQL Server. All the parameters in the stored procedure are exposed in the corresponding operation. The OUT parameter contains the return value of the stored procedure. The result set of the stored procedure is an array of DataSet. For more information about DataSet, see [http://go.microsoft.com/fwlink/?LinkId=196853](http://go.microsoft.com/fwlink/?LinkId=196853). The schema information of the target object is obtained as part of the response message at run time.  

 However, if you want to obtain the schema information of the target object at design time, you must generate schemas for the procedures under the **Strongly-Typed Procedures** node in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Note that the same stored procedures are surfaced under the **Procedures** and the **Strongly-Typed Procedures** node. The return value of the stored procedure is strongly typed, and not just an array of DataSet. As the schema information is available at the design time, you can use it to map the schema of the stored procedure to another schema for a different operation. For example, you can map the schema generated for a strongly-typed procedure to the schema generated for the Insert operation on a database table.  

> [!NOTE]
>  You will not be able to view the schema information at design time for a strongly-typed stored procedure if:  
> 
> - You are using a cursor, which is a return value of another stored procedure, as the input parameter for the strongly-typed stored procedure.  
>   -   It is a CLR stored procedure that performs some operations on a table.  

## Support for Stored Procedures with FOR XML Clause  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] also enables you to execute stored procedures that have a SELECT statement with a FOR XML clause. A FOR XML clause is used in a SELECT statement to return the results as XML instead of a rowset. For more information about the FOR XML clause, see [http://go.microsoft.com/fwlink/?LinkId=131402](http://go.microsoft.com/fwlink/?LinkId=131402).  

> [!NOTE]
>  The “native” [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] available with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supports only those stored procedures that return XML, that is, have the FOR XML clause in the SELECT statement. With the support for stored procedures with FOR XML clause, you can execute these stored procedures using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] without making any changes to the stored procedure definition.  

## Support for Stored Procedures with Temporary Tables  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables you to generate metadata for stored procedures that contain temporary tables in their definitions. However, for such stored procedures you must generate metadata by selecting the stored procedures only from the **Procedures** node, while using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The adapter does not support generating metadata for such stored procedures from under the **Strongly-Typed Procedures** node.  

## Support for Result Sets Containing Columns Without Names or With Same Names  
 The following table lists how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] handles columns without names and same names in the result sets for stored procedures and strongly-typed stored procedures.  


|    Result set contains…     |                                                                                                                                                       Stored Procedure                                                                                                                                                       |                                                                                                           Strongly-Typed Stored Procedure                                                                                                            |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Columns without names**  | The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] generates a name for the column in the following way: a unique ID (GUID) is generated for the column without "-" (hyphen), and then the GUID string is prefixed by "C" because the generated GUID might start with a digit but an XML tag name cannot. |                                The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] generates the following name for the column: “UnNamedColumn[column_index]”,  where column_index starts from ‘0’.                                |
| **Columns with same names** |                                                                                The names of the columns other than the first one are appended with “*” (underscore) followed by a random GUID without "-" (hyphen). For example: “\\*[GUID]”.                                                                                | The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support columns with same names in the result sets, and throws an exception. **Important:**  You must ensure that the column names in a result set have unique names. |

> [!NOTE]
>  In general, it is recommended that all the columns in a result set for stored procedures and strongly-typed stored procedures must be named, and have unique names.  

 For more information about:  

-   How to execute stored procedures, see [Execute stored procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  

-   How to execute stored procedures having a FOR XML clause, see [Execute stored procedures having a FOR XML clause in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md).  

-   Message schemas for the stored procedures, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  

## See Also  
 [Connect to an SAP system using the adapter](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)