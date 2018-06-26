---
title: "Step 1: Generate Schema for Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63218a5e-9af2-40af-9992-ac5e204d2832
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Generate Schema for Operations
![Step 1 of 2](../../adapters-and-accelerators/adapter-sql/media/step-1of2.gif "Step_1of2")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you generate schemas for the operations that you perform on the SQL Server database using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For this tutorial, you must generate schema for the following:  
  
-   **Notification** (inbound operation).  
  
-   **UPDATE_EMPLOYEE** stored procedure (outbound operation).  
  
-   **Insert** operation on the **Purchase_Order** table (outbound operation).  
  
## Prerequisites  
 Before you proceed with the tutorial, make sure:  
  
-   You must have completed the steps in [Before You Develop BizTalk Applications](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).  
  
-   You must log on as a member of the BizTalk Server Administrators group.  
  
### To generate schema for operations  
  
1. Create a new BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. For this tutorial, name the project as `Employee_PurchaseOrder`.  
  
2. Connect to the ADAPTER_SAMPLES SQL Server database using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. For instructions on how to connect using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Connect to SQL Server in Visual Studio Using Consume Adapter Service Add-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).  
  
   > [!NOTE]
   >  You can also connect to SQL Server using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. However, for this tutorial you will use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
3. Generate schema for the **Notification** inbound operation.  
  
   1. After connecting to the ADAPTER_SAMPLES database, in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], from the **Select contract type** list, select **Service (Inbound operations)**.  
  
   2. From the **Select a category** box, click the root node (**/**).  
  
   3. From the **Available categories and operations** box, select **Notification** and click **Add**. The **Notification** operation is now displayed in the **Added categories and operations** box. Click **OK**.  
  
4. Generate schema for the **UPDATE_EMPLOYEE** stored procedure and the Insert operation on **Purchase_Order** table.  
  
   1. Repeat step 2 to connect to ADAPTER_SAMPLES database in SQL Server using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
      > [!NOTE]
      >  You cannot generate schema for inbound and outbound operations at the same time. Hence, in step 3, after you click **OK** to generate the schema for **Notification** operation, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] closes. You must reconnect to the SQL Server database to generate schema for outbound operations.  
  
   2. From the **Select contract type** list, select **Client (Outbound operations)**.  
  
   3. From the **Select a category** box, click the **Strongly-Typed Procedures** node. From the **Available categories and operation**s box, select **UPDATE_EMPLOYEE**, and then click **Add**.  
  
      > [!IMPORTANT]
      >  The **UPDATE_EMPLOYEE** stored procedure is also available under the **Procedures** node. However, if you generate schema for the stored procedure from under the **Procedures** node, the response message schema is not available at design-time but is received with the response message after you execute the stored procedure.  
      >   
      >  In this tutorial, you will map the response schema of the stored procedure to the input schema of the Insert operation on the **Purchase_Order** table. Therefore, you will need the schema for the **UPDATE_EMPLOYEE** stored procedure at design-time and you must select the stored procedure from under the **Strongly-Typed Procedures**. By doing so, you will get the schema of the stored procedure at design-time.  
  
   4. From the **Select a category** box, expand the **Tables** node, and click the node for **Purchase_Order** table. From the **Available categories and operation**s box, select **Insert**, click **Add**, and then click **OK**.  
  
## What did I just do?  
 In this step, you generated schemas for **Notification** (inbound operation), **UPDATE_EMPLOYEE** stored procedure, and **Insert** operation on the **Purchase_Order** table. After you generate the schema, the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] adds the following files to your BizTalk project:  
  
- XSD files that contain schema for the request message to invoke operations on SQL Server.  
  
- XML binding files that you can use to create WCF-Custom send and receive ports in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
  For more information about generating schemas, see [Browse, search, and get metadata for SQL operations using the SQL adapter](../../adapters-and-accelerators/adapter-sql/browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter.md).  
  
## Next Steps  
 You create messages in the BizTalk project for the schemas in [Step 2: Create Messages for BizTalk Orchestrations](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).  
  
## See Also  
 [Lesson 1: Generate Schemas and Create Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)