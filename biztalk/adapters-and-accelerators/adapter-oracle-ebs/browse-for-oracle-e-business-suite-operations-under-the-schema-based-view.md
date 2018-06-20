---
title: "Browse for Oracle E-Business Suite operations under the schema-based view | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d004a99f-0db1-4cdb-80cd-ea71de4e1098
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse for Oracle E-Business Suite operations under the schema-based view
You can use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to browse for outbound and inbound operations that can be performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. This topic provides information on how to browse for outbound and inbound operations under the schema-based view.  
  
> [!NOTE]
>  The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] present essentially the same interface when you browse and search for operations, so both components are covered in the same topics.  
  
## Prerequisites  
 You must connect to the Oracle E-Business Suite before you can browse metadata for target operations. For information about how to connect to the Oracle database when you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## Browsing for Outbound Operations  
 Perform the following steps to browse the outbound operations under the schema-based view.  
  
#### To browse metadata for outbound operations under the Schema-Based view  
  
1. Connect to Oracle E-Business Suite using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** list, for outbound operations select **Client (Outbound operations)**.  
  
3. The **Select a category** box lists the different views under which the Oracle E-Business Suite artifacts are categorized.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The root node (/) is selected, and the general category nodes available under the root node are listed in the **Available categories and operations** box.  
  
    ![Operations and categories at the root level](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
   > [!NOTE]
   >  The standard operations such as ExecuteReader, ExecuteScalar, and ExecuteNonQuery are available at the root level. For more information about these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md). For instructions on how to execute these operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
4. Expand the **Schema-Based View** node to see the schemas defined in the underlying database. Each schema is further categorized on the basis of PL-SQL APIs, procedures, functions, tables, and views it contains.  
  
   > [!TIP]
   >  You can directly go to the “immediate” category node or subcategory nodes in the tree, by typing the name of the artifact while the focus is on the tree view in the **Select a category** box. For example, to jump to the **SCOTT** schema, keep the focus on the **Schema-Based View** node, and then type `SCOTT`.  
  
5. Expand the **PL-SQL APIs** node to see the list of packages defined in the Oracle database for a particular schema. Click a package name to see the functions and procedures defined within that package in the **Available categories and operations** box.  
  
    ![Browse packages in the Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/582a9bd7-beed-4b36-b465-f5c4ceb6e740.gif "582a9bd7-beed-4b36-b465-f5c4ceb6e740")  
  
6. Click the **Procedures** node to see the list of procedures in the **Available categories and operations** box.  
  
    ![Browse procedures in Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/7213154e-6a26-4fc3-b4ec-1658779f77d3.gif "7213154e-6a26-4fc3-b4ec-1658779f77d3")  
  
7. Click the **Functions** node to see the list of functions in the **Available categories and operations** box.  
  
    ![Browse funcitons in Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/5df9b42c-9d8b-4c81-a0ae-ba5336445837.gif "5df9b42c-9d8b-4c81-a0ae-ba5336445837")  
  
8. Expand the **Tables** node to see the list of tables for a particular schema. Click a table name to see the operations supported on the table in the **Available categories and operations** box.  
  
    ![Browse for tables in Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/94dd4642-1178-4d88-986b-f0ad409c414c.gif "94dd4642-1178-4d88-986b-f0ad409c414c")  
  
   > [!NOTE]
   >  If a table contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The name of such operations are Read_\<LOBColName\>. For example, if the table has a column, PHOTO, of type BLOB, the adapter exposes a **Read_PHOTO** operation. If a table has more than one column of type BLOB, CLOB, NCLOB, and BFILE the adapter will expose as many number of Read_\<LOBColName\> operations.  
   >   
   >  Similarly, if a table contains columns of type BLOB, CLOB, or NCLOB the adapter also exposes a specific operation to update data into such columns. The name of such operations are Update_\<LOBColName\>. For example, if the table has a column, PHOTO, of type BLOB, the adapter exposes an **Update_PHOTO** operation. If a table has more than one column of type BLOB, CLOB, and NCLOB the adapter will expose as many number of Update_\<LOBColName\> operations. Note that the update operation is not supported on columns of type BFILE.  
  
9. Expand the **Views** node to see the list of views for a particular schema. Click a view name to see the operations supported on the view in the **Available categories and operations** box.  
  
     ![Browse for views in Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/e1893e48-065c-4642-b076-192758d103db.gif "e1893e48-065c-4642-b076-192758d103db")  
  
    > [!NOTE]
    >  If a view contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The name of such operations are Read_\<LOBColName\>. For example, if the view has a column, RULE, of type BLOB, the adapter exposes a **Read_RULE** operation. If a view has more than one column of type BLOB, CLOB, NCLOB, or BFILE the adapter will expose as many number of Read_\<LOBColName\> operations. Note that Update_\<LOBColName\> operations are not supported on views.  
  
## Browsing for Inbound Operations  
 Perform the following steps to browse the inbound operations under the schema-based view.  
  
#### To browse metadata for inbound operations under the Schema-based view  
  
1. Connect to Oracle E-Business Suite using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** list, for inbound operations select **Service (Inbound operations)**.  
  
3. The **Select a category** box lists the different views under which the Oracle E-Business Suite artifacts are categorized.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The root node (/) is selected, and the general category nodes available under the root node are listed in the **Available categories and operations** box.  
  
    ![Inbound operation at the root level](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
    The inbound operation, **Notification**, is also available at the root level.  
  
4. Expand the **Schema-Based View** node to see the schemas defined in the underlying database. Each schema is further categorized on the basis of PL-SQL APIs, procedures, functions, tables, and views it contains.  
  
   > [!TIP]
   >  You can directly go to the “immediate” category node or subcategory nodes in the tree, by typing the name of the artifact while the focus is on the tree view in the **Select a category** box. For example, to jump to the **SCOTT** schema, keep the focus on the **Schema-Based View** node, and then type `SCOTT`.  
  
5. Expand the **PL-SQL APIs** node to see the list of packages defined in the Oracle database for a particular schema. Click a package name to see the functions and procedures defined within that package in the **Available categories and operations** box. Each of the listed functions and procedures can be used to poll the Oracle database.  
  
    ![Browse packages in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/ab45e4a3-1425-4b23-afc2-8aecef546802.gif "ab45e4a3-1425-4b23-afc2-8aecef546802")  
  
6. Click the **Procedures** node to see the list of procedures in **the Available categories and operations** box. Each of the listed procedures can be used to poll the Oracle database.  
  
    ![Browse procedures in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/04538693-5abf-4162-82e9-4107b4088b56.gif "04538693-5abf-4162-82e9-4107b4088b56")  
  
7. Click the **Functions** node to see the list of functions in the **Available categories and operations** box. Each of the listed functions can be used to poll the Oracle database.  
  
    ![Browse functions in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b.gif "b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b")  
  
8. Expand the **Tables** node to see the list of tables for a particular schema. Click a table name to see the **Poll** inbound operation supported on the table in the **Available categories and operations** box.  
  
    ![Browse tables in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/58e9315d-3194-4a01-a505-bd1514e9d7e3.gif "58e9315d-3194-4a01-a505-bd1514e9d7e3")  
  
9. Expand the **Views** node to see the list of views for a particular schema. Click a view name to see the **Poll** inbound operation supported on the view in the **Available categories and operations** box.  
  
     ![Browse views in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/f1282f17-efbe-43e6-90fa-5676e04051e8.gif "f1282f17-efbe-43e6-90fa-5676e04051e8")  
  
## See Also  
 [Browse, search, and get metadata for Oracle E-Business Suite operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)