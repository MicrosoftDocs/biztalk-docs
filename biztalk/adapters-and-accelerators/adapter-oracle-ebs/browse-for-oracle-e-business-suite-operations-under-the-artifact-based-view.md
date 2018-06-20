---
title: "Browse for Oracle E-Business Suite operations under the artifact-based view | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 962ac1cc-826c-46d6-848a-4cd371804596
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse for Oracle E-Business Suite operations under the artifact-based view
You can use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to browse for outbound and inbound operations that can be performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. This topic provides information on how to browse for outbound and inbound operations under the artifact-based view.  
  
> [!NOTE]
>  The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] present essentially the same interface when you browse and search for operations, so both components are covered in the same topics.  
  
## Prerequisites  
 You must connect to the Oracle E-Business Suite before you can browse metadata for target operations. For information about how to connect to the Oracle database when you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## Browsing for Outbound Operations  
 Perform the following steps to browse the outbound operations under the artifact-based view.  
  
#### To browse metadata for outbound operations under the Artifact-Based view  
  
1. Connect to Oracle E-Business Suite using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** list, for outbound operations select **Client (Outbound operations)**.  
  
3. The **Select a category** box lists the different views under which the Oracle E-Business Suite artifacts are categorized.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The root node (/) is selected, and the general category nodes available under the root node are listed in the **Available categories and operations** box.  
  
    ![Operations and categories at the root level](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
   > [!NOTE]
   >  The standard operations such as ExecuteReader, ExecuteScalar, and ExecuteNonQuery are available at the root level. For more information about these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md). For instructions on how to execute these operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
4. Expand the **Artifact-Based View** node to see category for artifacts, both for the Oracle E-Business Suite and the underlying database. Each category is further categorized based on the application it belongs to (for Oracle-E-Business Suite artifacts such as interface table, interface views, concurrent programs, and request sets) or the schema it belongs to (for Oracle database artifacts such as PL-SQL APIs, procedures, functions, tables, and views).  
  
   > [!TIP]
   >  You can directly go to the “immediate” category node or subcategory nodes in the tree, by typing the name of the artifact while the focus is on the tree view in the **Select a category** box. For example, to jump to the **Procedures** node, keep the focus on the **Artifact-Based View** node, and then type `Procedures`.  
  
5. Expand the **Interface Tables** node to see all the Oracle E-Business Suite applications. Expand an Oracle E-Business suite application to list all the interface tables belonging to that application. Click an interface table name to see operations available for the table in the **Available categories and operations** box.  
  
   > [!NOTE]
   >  If an interface table contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The name of such operations are Read_\<LOBColName\>. For example, if the interface table has a column, FILE_DATA, of type BLOB, the adapter exposes a **Read_FILE_DATA** operation. If an interface table has more than one column of type BLOB, CLOB, NCLOB, and BFILE the adapter will expose as many number of Read_\<LOBColName\> operations.  
   >   
   >  Similarly, if an interface table contains columns of type BLOB, CLOB, or NCLOB the adapter also exposes a specific operation to update data into such columns. The name of such operations are Update_\<LOBColName\>. For example, if the interface table has a column, FILE_DATA, of type BLOB, the adapter exposes an **Update_FILE_DATA** operation. If an interface table has more than one column of type BLOB, CLOB, and NCLOB the adapter will expose as many number of Update_\<LOBColName\> operations. Note that the update operation is not supported on columns of type BFILE.  
  
6. Expand the **Interface Views** node to see all the Oracle E-Business Suite applications. Expand an Oracle E-Business suite application to list all the interface views belonging to that application. Click an interface view name to see operations available for the view in the **Available categories and operations** box.  
  
   > [!NOTE]
   >  If an interface view contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The names of such operations are Read_\<LOBColName\>. For example, if the interface view has a column, FILE_CONTENT, of type BLOB, the adapter exposes a **Read_FILE_CONTENT** operation. If an interface view has more than one column of type BLOB, CLOB, NCLOB, or BFILE the adapter will expose as many number of Read_\<LOBColName\> operations. Note that Update_\<LOBColName\> operations are not supported on views.  
  
7. Expand the **Concurrent Programs** node to see all the Oracle E-Business Suite applications. Click an Oracle E-Business suite application to list all the concurrent programs belonging to that application in the **Available categories and operations** box.  
  
   > [!IMPORTANT]
   >  The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) displays friendly names of concurrent programs. However, the metadata for the concurrent program has the actual name of the concurrent program. For example, the Receivables application contains a “Customer Interface” concurrent program. However, the metadata has the concurrent program name as RACUST, which is the actual name of the concurrent program.  
  
8. Expand the **Request Sets** node to see all the Oracle E-Business Suite applications. Click an Oracle E-Business suite application to list all the request sets belonging to that application in the **Available categories and operations** box.  
  
   > [!IMPORTANT]
   >  The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) displays friendly names of request sets. However, the metadata for the request set has the actual name of the request set. For example, the Applications DBA application contains a “DownloadPatches” request set. However, the metadata has the request set name as FNDRSSUB1623, which is the actual name of the request set.  
  
9. Expand the **PL-SQL APIs** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all packages defined for that schema. Click a package name to see the functions and procedures within the package in the **Available categories and operations** box.  
  
     ![Browse packages in the Oracle database](../../adapters-and-accelerators/adapter-oracle-ebs/media/7a9dc061-db0b-4a8e-bfc6-3a003ad687d8.gif "7a9dc061-db0b-4a8e-bfc6-3a003ad687d8")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of packages defined for that schema. Click a package name to see the functions and procedures within the package in the **Available categories and operations** box.  
  
     ![Browse packages in Oracle database for all schemas](../../adapters-and-accelerators/adapter-oracle-ebs/media/09a4841b-b88f-490d-a49a-94e392b5493c.gif "09a4841b-b88f-490d-a49a-94e392b5493c")  
  
10. Expand the **Procedures** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Click the **Current Schema (\<schema name\>)** node to see all the procedures defined for that schema in the **Available categories and operations** box.  
  
     ![Browse procedures in Oracle database for a schema](../../adapters-and-accelerators/adapter-oracle-ebs/media/6d78563a-53f7-45cc-8652-f40d4703bdf4.gif "6d78563a-53f7-45cc-8652-f40d4703bdf4")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Click a schema node to see a list of procedures defined for that schema in the **Available categories and operations** box.  
  
     ![Browse procedures in Oracle database for schemas](../../adapters-and-accelerators/adapter-oracle-ebs/media/a514d199-d6c1-44a0-bf6b-28ddf702081a.gif "a514d199-d6c1-44a0-bf6b-28ddf702081a")  
  
11. Expand the **Functions** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Click the **Current Schema (\<schema name\>)** node to see all the functions defined for that schema in the **Available categories and operations** box.  
  
     ![Browse functions in Oracle database for a schema](../../adapters-and-accelerators/adapter-oracle-ebs/media/22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd.gif "22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Click a schema node to see a list of functions defined for that schema in the **Available categories and operations** box.  
  
     ![Browse functions in Oracle database for all schema](../../adapters-and-accelerators/adapter-oracle-ebs/media/b4d29036-3d37-4a50-82c2-3532adbe2875.gif "b4d29036-3d37-4a50-82c2-3532adbe2875")  
  
12. Expand the **Tables** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all the tables defined for that schema. Click a table name to see the operations supported on that table in the **Available categories and operations** box.  
  
     ![Browse tables in Oracle database for a schema](../../adapters-and-accelerators/adapter-oracle-ebs/media/6ba7420f-9893-4b3e-91cb-10f29d725ad3.gif "6ba7420f-9893-4b3e-91cb-10f29d725ad3")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of tables defined for that schema. Click a table name to see the operations supported on that table in the **Available categories and operations** box.  
  
     ![Browse Oracle database tables for all schemas](../../adapters-and-accelerators/adapter-oracle-ebs/media/d7c52ab4-ba27-404a-9db6-32b2a635ad2f.gif "d7c52ab4-ba27-404a-9db6-32b2a635ad2f")  
  
    > [!NOTE]
    >  If a table contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The name of such operations are Read_\<LOBColName\>. For example, if the table has a column, PHOTO, of type BLOB, the adapter exposes a **Read_PHOTO** operation. If a table has more than one column of type BLOB, CLOB, NCLOB, and BFILE the adapter will expose as many number of Read_\<LOBColName\> operations.  
    >   
    >  Similarly, if a table contains columns of type BLOB, CLOB, or NCLOB the adapter also exposes a specific operation to update data into such columns. The name of such operations are Update_\<LOBColName\>. For example, if the table has a column, PHOTO, of type BLOB, the adapter exposes an **Update_PHOTO** operation. If a table has more than one column of type BLOB, CLOB, and NCLOB the adapter will expose as many number of Update_\<LOBColName\> operations. Note that the update operation is not supported on columns of type BFILE.  
  
13. Expand the **Views** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all the views defined for that. Click a view name to see the operations supported on that view in the **Available categories and operations** box.  
  
     ![Browse views in Oracle database for current schema](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a38cfed-007d-431a-af60-c9c8be5369ab.gif "2a38cfed-007d-431a-af60-c9c8be5369ab")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of views defined for that schema. Click a view name to see the operations supported on that view in the **Available categories and operations** box.  
  
     ![Browse views in Oracle database for all schemas](../../adapters-and-accelerators/adapter-oracle-ebs/media/67ca336c-62ac-4374-87da-07cf331ea4ad.gif "67ca336c-62ac-4374-87da-07cf331ea4ad")  
  
    > [!NOTE]
    >  If a view contains columns of type BLOB, CLOB, NCLOB, or BFILE the adapter also exposes a specific operation to read data from such columns. The name of such operations are Read_\<LOBColName\>. For example, if the view has a column, RULE, of type BLOB, the adapter exposes a **Read_RULE** operation. If a view has more than one column of type BLOB, CLOB, NCLOB, or BFILE the adapter will expose as many number of Read_\<LOBColName\> operations. Note that Update_\<LOBColName\> operations are not supported on views.  
  
## Browsing for Inbound Operations  
 Perform the following steps to browse the inbound operations under the artifact-based view.  
  
#### To browse metadata for inbound operations under the Artifact-based view  
  
1. Connect to Oracle E-Business Suite using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** list, for inbound operations select **Service (Inbound operations)**.  
  
3. The **Select a category** box lists the different views under which the Oracle E-Business Suite artifacts are categorized.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The root node (/) is selected, and the general category nodes available under the root node are listed in the **Available categories and operations** box.  
  
    ![Inbound operation at the root level](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
    The inbound operation, **Notification**, is also available at the root level.  
  
4. Expand the **Artifact-Based View** node to see category for artifacts, both for the Oracle E-Business Suite and the underlying database. Each category is further categorized based on the application it belongs to (for Oracle-E-Business Suite artifacts such as interface table and interface views) or the schema it belongs to (for Oracle database artifacts such as PL-SQL APIs, procedures, functions, tables, and views).  
  
   > [!TIP]
   >  You can directly go to the “immediate” category node or subcategory nodes in the tree, by typing the name of the artifact while the focus is on the tree view in the **Select a category** box. For example, to jump to the **Procedures** node, keep the focus on the **Artifact-Based View** node, and then type `Procedures`.  
   > 
   > [!NOTE]
   >  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not surface concurrent programs and request sets for inbound operations.  
  
5. Expand an Oracle application to see categories for interface tables and interface views available for that application. Expand the **Interface Tables** and **Interface Views** nodes to see the interface tables and interface views for the Oracle application. Click an interface table or interface view to see the inbound operation available for the table or view in the **Available categories and operations** box.  
  
    In the following figure, an interface view is selected in the **Select a category** box and the inbound operation supported on the view is listed in the **Available categories and operations** box.  
  
    ![Inbound operations on interface views](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
6. Expand the **PL-SQL APIs** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all packages defined for that schema. Click a package name to see the functions and procedures within the package in the **Available categories and operations** box. Each of the listed functions and procedures can be used to poll the Oracle database.  
  
    ![Browse PL&#45;SQL APIs in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a.gif "4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a")  
  
    Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of packages defined for that schema. Click a package name to see the functions and procedures within the package in the **Available categories and operations** box. Each of the listed functions and procedures can be used to poll the Oracle database.  
  
    ![Browse PL&#45;SQL APIs for all schemas for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/e28a803e-fcfb-4021-9225-924d54a484c0.gif "e28a803e-fcfb-4021-9225-924d54a484c0")  
  
7. Expand the **Procedures** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Click the **Current Schema (\<schema name\>)** node to see all the procedures defined for that schema in the **Available categories and operations** box. Each of the listed procedures can be used to poll the Oracle database.  
  
    ![Browse procedures for all schemas for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/5e78da80-d99a-44d3-8eac-f636828f8ceb.gif "5e78da80-d99a-44d3-8eac-f636828f8ceb")  
  
    Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Click a schema node to see a list of procedures defined for that schema in the **Available categories and operations** box. Each of the listed procedures can be used to poll the Oracle database.  
  
    ![Browse procedures in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/22d8e866-ed19-49f4-a6eb-683343b16cf5.gif "22d8e866-ed19-49f4-a6eb-683343b16cf5")  
  
8. Expand the **Functions** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Click the **Current Schema (\<schema name\>)** node to see all the functions defined for that schema in the **Available categories and operations** box. Each of the listed functions can be used to poll the Oracle database.  
  
    ![Browse functions in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf.gif "64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf")  
  
    Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Click a schema node to see a list of functions defined for that schema in the **Available categories and operations** box.  Each of the listed functions can be used to poll the Oracle database.  
  
    ![Browse functions in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/1d22c3c8-8c24-4905-8144-bdb4840244f1.gif "1d22c3c8-8c24-4905-8144-bdb4840244f1")  
  
9. Expand the **Tables** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all the tables defined for that schema. Click a table name to see the **Poll** inbound operation supported on that table in the **Available categories and operations** box.  
  
     ![Browse tables in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/7c60dfbf-3836-4e72-abe8-5f32a0936807.gif "7c60dfbf-3836-4e72-abe8-5f32a0936807")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of tables defined for that schema. Click a table name to see the **Poll** inbound operation supported on that table in the **Available categories and operations** box.  
  
     ![Browse tables in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/c5fbaf59-2e79-4141-8a85-1e1b8eedcea7.gif "c5fbaf59-2e79-4141-8a85-1e1b8eedcea7")  
  
10. Expand the **Views** node to see category nodes for the current user schema (with which you login) and all other schemas defined in the underlying Oracle database. Expand the **Current Schema (\<schema name\>)** node to see all the views defined for that. Click a view name to see the **Poll** inbound operation supported on that view in the **Available categories and operations** box.  
  
     ![Browse views in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/2299de79-9f50-433d-9e71-164f6d02bd78.gif "2299de79-9f50-433d-9e71-164f6d02bd78")  
  
     Similarly, expand the **All Schemas** node to see a list of all the schemas defined in the Oracle database. Expand a schema node to see a list of views defined for that schema. Click a view name to see the **Poll** inbound operation supported on that view in the **Available categories and operations** box.  
  
     ![Browse views in Oracle database for polling](../../adapters-and-accelerators/adapter-oracle-ebs/media/860e6636-1ef6-42ad-a0e2-d661e632b624.gif "860e6636-1ef6-42ad-a0e2-d661e632b624")  
  
## See Also  
 [Browse, search, and get metadata for Oracle E-Business Suite operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)