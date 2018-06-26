---
title: "Building Blocks to develop BizTalk Applications with Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "developing, BizTalk applications"
  - "run-time tasks"
  - "design-time tasks"
ms.assetid: ad9ca856-5569-41ab-8617-ae6db5e3b4d7
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Building Blocks to develop BizTalk Applications with Oracle Database
Performing operations on an Oracle database by using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] involves two sets of tasks: design-time and run-time.  
  
## Design-time tasks  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides capability to browse, search, and retrieve the Oracle metadata for tables, stored procedures, and other such items in the form of XML Schema definition languages (XSDs) by using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. The XSDs are specific to the operation you want to perform on the Oracle database. The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] is available only when you create a BizTalk project. At design time you need to perform the following tasks:  
  
- **Create BizTalk project and generate schema**. You must create a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and generate the schema for the operation that will be performed on the Oracle database. For example, if you want to insert a record into the EMPLOYEE table, you must generate the metadata for the Insert operation for the EMPLOYEE table. In this step, you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema. For more information, see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).
  
- **Set up an orchestration**. Once you have generated the schema, you must set up an orchestration by using the Orchestration Designer. For a basic orchestration, you add the Send and Receive shapes along with the Send and Receive logical ports. In later steps, you map these logical ports to physical ports by using the BizTalk Server Administration console. The orchestration uses these ports to pick messages that an adapter client sends. The orchestration then passes the messages to the Oracle database. Once a response is received from the Oracle database, the orchestration passes the response to the adapter client.  
  
- **Create messages and link to schema**. In your orchestration, you must create messages that will be mapped to the schema you generated in the first step. Typically, you create a request message and a response message. These messages are mapped to corresponding request and response schemas.  
  
- **Map message shapes to messages and ports**. In your orchestration, you must now map each shape that you added in the second step to messages that you created in the third step. You must also map a message shape to the port on which that message will be sent.  
  
   For example, if the first shape in your orchestration is a Receive shape that will receive a message, you map this shape to a request message and the port that sends the request message.  
  
- **Build and deploy the BizTalk project**. After you have set up the orchestration and mapped messages, ports, and schemas, you must build the BizTalk solution. For building a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you need an assembly key file. After you successfully build the solution, you must deploy the solution.  
  
  > [!NOTE]
  >  More detailed description of these high-level tasks, including procedural information, is provided in various topics of this section.  
  
  Once the solution is deployed, your design-time tasks are accomplished. You must now perform the run-time tasks.  
  
## Run-time tasks  
 At run time, you can use the BizTalk Server Administration console to deploy and monitor the orchestration you created at design time. In addition, you must:  
  
- **Configure the application**. The BizTalk project you deployed at design time shows up in the BizTalk Server Administration console as an orchestration. You must configure this orchestration by mapping the logical ports you created at design time to physical ports that you must now create using the BizTalk Server Administration console.  
  
   On the physical ports, you must specify an "action" or "action mapping". This action corresponds to the operation you want to perform on the Oracle database. You need to set the action if you are not using dynamic actions.  
  
- **Start the application**. After the application is configured, you must start the application, and drop input messages at a defined file location. The orchestration consumes the input messages and passes them to the Oracle database and receives a response. This response will be available to you at another defined file location.  
  
  To accomplish these high-level design-time and run-time tasks, you must also perform other tasks. For example, when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate the schema, you must specify a connection URI to connect to the Oracle database. This section provides information on such repetitive tasks that you must perform as you develop BizTalk applications using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  

  
## See Also  
[Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)