---
title: "Building blocks to create Oracle E-Business Suite applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 483a52d4-1aaf-46b1-bb42-9f91bf678346
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Building blocks to create Oracle E-Business Suite applications
To perform operations on Oracle E-Business Suite by using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must perform a set of design-time and run-time tasks using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console respectively. This section provides an overview of these tasks. All the topics in this section, which demonstrate how to perform specific operations on Oracle E-Business Suite using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], are modeled on these high-level tasks.  
  
## Using Visual Studio  
  
1. **Create BizTalk project, and generate schema**. You must create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and generate schema for the operation that you will perform on Oracle E-Business Suite. For example, if you want to select records from an Oracle E-Business Suite interface table, you must generate schema for the Select operation for that table. To generate schema, you must use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. For more information, see [Retrieving Metadata for Oracle E-Business Suite Operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
2. **Set up an orchestration**. Once you have generated the schema, you must set up an orchestration by using the Orchestration Designer. For a basic orchestration, you add the Send and Receive shapes along with the Send and Receive logical ports. In later steps, you map these logical ports to physical ports by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. The orchestration uses these ports to pick messages that an adapter client sends. The orchestration then passes the messages to Oracle E-Business Suite. Once Oracle E-Business Suite sends a response, the orchestration passes the response back to the adapter client.  
  
3. **Create messages, and link to schema**. In your orchestration, you must create messages that will be mapped to the schema you generated in the first step. Typically, you create a request message and a response message. These messages are mapped to the corresponding request and response schemas.  
  
4. **Map message shapes to messages and ports**. In your orchestration, you must now map each shape that you added in the second step to messages that you created in the third step. You must also map a message shape to the port on which that message will be sent.  
  
    For example, if the first shape in your orchestration is a Receive shape that will receive a message, you map this shape to a request message and the port that sends the request message.  
  
5. **Build and deploy the BizTalk project**. After you have set up the orchestration and mapped messages, ports, and schemas, you must build the BizTalk solution. For building a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you need an assembly key file. After you successfully build the solution, you must deploy the solution.  
  
> [!NOTE]
>  More detailed description of these high-level tasks, including procedural information, is provided in various topics of this section.  
  
 Once you have successfully built and deployed the BizTalk project, your design-time tasks in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] are accomplished. You must now perform certain run-time tasks using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Using the BizTalk Server Administration Console  
  
1. **Configure the application**. The BizTalk project you deployed by using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] shows up in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console as an orchestration. You must configure this orchestration by mapping the logical ports you created in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to physical ports that you must now create using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
    On the physical ports, you must specify an "action" or "action mapping". This action corresponds to the operation you want to perform on Oracle E-Business Suite. You need to specify the action if you are not using dynamic actions. For more information about actions, see [Configure the SOAP Action for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md).  
  
2. **Start the application**. After the application is configured, you must start the application, and drop request messages at a defined file location. The orchestration consumes the request messages, passes them to Oracle E-Business Suite, and receives a response. This response is available to the adapter client at another defined file location.  
  
   To accomplish these high-level tasks, you must also perform other tasks. For example, when you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema, you must specify a connection URI to connect to Oracle E-Business Suite. This section provides information on such repetitive tasks that you must perform as you develop BizTalk applications using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
## In This Section  
  
-   [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)  
  
-   [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md)  
  
-   [Configure the Sign-in Credentials for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md)  
  
-   [Configure the Binding Properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)  
  
-   [Configure the SOAP Action for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md)  
  
-   [Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)  
  
-   [Configure a Physical Port Binding Using a Port Binding File to Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)  
  
-   [Configure Dynamic Ports with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-dynamic-ports-with-oracle-e-business-suite.md)  
  
-   [Reuse Adapter Bindings with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)  
  
## See Also  
 [Developing BizTalk Applications](../../core/developing-biztalk-server-applications.md)