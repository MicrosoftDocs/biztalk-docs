---
title: "Operations on Synonyms2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bc9b2c4-ac22-491b-bc64-95e08a39b74d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Synonyms
The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] allows you to perform operations on synonyms. A synonym is an alias or friendly name for the database objects (such as tables, views, stored procedures, functions, and packages). For more information about synonyms in Oracle, see [http://go.microsoft.com/fwlink/?LinkId=138058](http://go.microsoft.com/fwlink/?LinkId=138058).  
  
## Advantages of Using Synonyms  
 Synonyms are helpful in the following scenarios:  
  
-   **Working with different schemas**: If you are working with different schemas, and need to access the objects across schemas, you have to use different SQL statements to access those objects. You can create a synonym for an object in a schema, and use the synonym in your SQL statement to access the object. If you need to access the underlying object in a different schema, modify the definition of the synonym to point to the object in a different schema. Thus, the applications based on the synonym continue to function without modification in the SQL statement.  
  
     For example, suppose you have two identical schemas for your test and production environments: “Test” and “Prod.” To access a table called “Employee” in the “Test” schema, you must use `Test.Employee` or `Employee` (if “Test” is the default schema) in your SQL statement. If you want to use the “Employee” table in the production schema, you must now use `Prod.Employee` or `Employee` (change the default schema to “Prod”) in your SQL statement. To get around this issue, you can create a synonym for the “Test.Employee” table (say “EMP”), and then use it in your SQL statements. Whenever you need to perform operation on the “Prod.Employee” table, modify the definition of the “EMP” synonym to point it to the “Prod.Employee” table. This ensures that you do not have to modify your SQL statements to perform operation on the object in different schemas.  
  
-   **Changes in the underlying objects**: The synonyms insulate you from any changes in the name or location of the underlying objects on which you are performing an operation. You can modify the synonym definition to accommodate any changes in the name or location of the underlying objects.  
  
     For example, suppose that you are using a table in one of your stored procedures. Now, if the table name changes or the table is moved to some other location then your stored procedure will stop working. To work around this, you can use a synonym for the table in the stored procedure, and update the synonym definition if there is a change in the name or location of the table.  
  
-   **Simplified and secure access**: In a distributed environment, you must use the schema name along with the object names to ensure that you are accessing the correct object. Moreover, you must also ensure that the user has required privileges on the target object. To simplify this, you can assign a simple name for an object by creating a synonym that has the full qualified path to the object, and then grant appropriate privileges on the synonym.  
  
## Working with Synonyms in the Adapter  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the synonyms in Oracle for:  
  
- Tables  
  
- Views  
  
- Stored Procedures  
  
- Functions  
  
- Packages  
  
  The synonyms for each of these artifacts are exposed alongside the respective underlying artifact in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For example, the **Tables** node under the **Schema-based view** will display all the synonyms for tables along with the database tables in a schema, the **Views** node under the **Schema-based view** will display all the synonyms for views along with the database views in a schema, and so on.  
  
- For synonyms created on tables and views, the same operations are exposed as for the underlying tables and views respectively. For example, if the underlying tables and views contain LOB columns, the synonyms for those tables and views will also expose the Read_\<LOBColName\> and Update_\<LOBColName\> operations for table synonyms and the Read_\<LOBColName\> operation for the view synonyms.  
  
- For synonyms created on stored procedures, functions, and packages, the synonyms are exposed as operations alongside the respective underlying stored procedures, functions, and packages in a schema.  
  
> [!NOTE]
>  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports only local synonyms. This implies that only those synonyms are supported by the adapter that target the artifacts on the local server.  
  
 Moreover, the message actions for the synonyms are the same as the underlying object except for the artifact name on which the action is performed. For example, the message action for the **Select** operation on a table in the SCOTT schema is: `Tables/Select/SCOTT/[TABLE_NAME]`. If you are performing a Select operation on a synonym for the same table in the SCOTT schema then the message action will be: `Tables/Select/SCOTT/[SYNONYM_NAME]`.  
  
 When you invoke an operation on a synonym in the adapter, the adapter calls the synonym in the Oracle database to execute the operation. However, the adapter uses the underlying object name in the synonym definition to fetch the metadata.  
  
 Synonyms can be used in normal outbound operations, composite operations, and polling.  
  
> [!NOTE]
>  You can search for synonyms in [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] just like other objects. However, you cannot search for procedures inside synonym packages from a skip-level node as you can do for the procedures inside packages. For information about searching for operations in the adapter, see [Browse, Search, and get metadata for SQL operations using the SQL adapter](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)