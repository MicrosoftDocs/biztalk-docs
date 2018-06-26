---
title: "Building blocks to develop BizTalk applications with the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fac7cbf4-b111-43ad-8726-36d037918c9c
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Building blocks to develop BizTalk applications with the SQL adapter
To perform operations on SQL Server by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must perform a set of design-time and run-time tasks using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console respectively. This section provides an overview of these tasks. All the topics in this section, which demonstrate how to perform specific operations on SQL Server using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], are modeled on these high-level tasks.  
  
## Using Visual Studio  
  
1. **Create BizTalk project, and generate schema**. You must create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and generate schema for the operation that you will perform on SQL Server. For example, if you want to insert records in a SQL Server table, you must generate schema for the Insert operation for that table. To generate schema, you must use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. For more information, see [Retrieving Metadata for SQL Server Operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
2. **Set up an orchestration**. Once you have generated the schema, you must set up an orchestration by using the Orchestration Designer. For a basic orchestration, you add the Send and Receive shapes along with the Send and Receive logical ports. In later steps, you map these logical ports to physical ports by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. The orchestration uses these ports to pick messages that an adapter client sends. The orchestration then passes the messages to SQL Server. Once SQL Server sends a response, the orchestration passes the response back to the adapter client.  
  
3. **Create messages, and link to schema**. In your orchestration, you must create messages that will be mapped to the schema you generated in the first step. Typically, you create a request message and a response message. These messages are mapped to the corresponding request and response schemas.  
  
4. **Map message shapes to messages and ports**. In your orchestration, you must now map each shape that you added in the second step to messages that you created in the third step. You must also map a message shape to the port on which that message will be sent.  
  
    For example, if the first shape in your orchestration is a Receive shape that will receive a message, you map this shape to a request message and the port that sends the request message.  
  
5. **Build and deploy the BizTalk project**. After you have set up the orchestration and mapped messages, ports, and schemas, you must build the BizTalk solution. For building a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you need an assembly key file. After you successfully build the solution, you must deploy the solution.  
  
> [!NOTE]
>  More detailed description of these high-level tasks, including procedural information, is provided in various topics of this section.  
  
 Once you have successfully built and deployed the BizTalk project, your tasks in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] are accomplished. You must now perform certain tasks using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Using the BizTalk Server Administration Console  
  
1. **Configure the application**. The BizTalk project you deployed by using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] shows up in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console as an orchestration. You must configure this orchestration by mapping the logical ports you created in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to physical ports that you must now create using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
    On the physical ports, you must specify an "action" or "action mapping". This action corresponds to the operation you want to perform on SQL Server. You need to specify the action if you are not using dynamic actions. For more information about actions, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).  
  
2. **Start the application**. After the application is configured, you must start the application, and drop request messages at a defined file location. The orchestration consumes the request messages, passes them to SQL Server, and receives a response. This response is available to the adapter client at another defined file location.  
  
   To accomplish these high-level tasks, you must also perform other tasks. For example, when you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema, you must specify a connection URI to connect to SQL Server. This section provides information on such repetitive tasks that you must perform as you develop BizTalk applications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## In This Section  
  
-   [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)  
  
-   [Configure the connection URI for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-connection-uri-for-the-sql-adapter.md)  
  
-   [Configure the sign in credentials for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-sign-in-credentials-for-the-sql-adapter.md)
  
-   [Configure the binding properties for the SQL adapter
](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md) 
  
-   [Configure the SOAP action for the SQL adapter
](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)
  
-   [Manually configure a physical port binding to the SQL adapter
](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md) 
  
-   [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)
  
-   [Configure dynamic ports](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)
  
-   [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)
  
## See Also  
[Develop BizTalk applications](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)