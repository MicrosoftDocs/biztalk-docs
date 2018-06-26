---
title: "Building blocks to create SAP applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "design-time tasks"
  - "run-time tasks"
  - "developing, fundamentals of (BizTalk applications)"
ms.assetid: 591a5597-5e7d-44b0-8bee-e1c987c5e6c3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Building blocks to create SAP applications
Performing operations on an SAP system using [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] involves two set of activities: design-time activities and run-time activities. To perform operations on an SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must perform a set of design-time and run-time tasks using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console respectively. This section provides an overview of these tasks. All the topics in this section, which demonstrate how to perform specific operations on an SAP system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], are modeled on these high-level tasks.  
  
## Design-time Tasks  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides capability to browse, search, and retrieve the SAP metadata for RFCs, BAPIs, and IDOCs in the form of XML Schema definition languages (XSDs) using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. The XSDs are specific to the operation you want to perform on the SAP system, and the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] is available only when you create a BizTalk project. At design time you need to perform the following tasks.  
  
- **Create BizTalk project and generate schema**. To start with, you must create a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and generate the schema for the RFC you will invoke in the SAP system. For example, if you want to invoke RFC_CUSTOMER_GET in the SAP system, you must generate the metadata for RFC_CUSTOMER_GET. In this step you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema. For more information, see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
- **Set up an orchestration**. Once you have generated the schema, you must set up an orchestration by using the Orchestration Designer. For a basic orchestration, you add the Send and Receive shapes along with the Send and Receive logical ports. In later steps, you map these logical ports to physical ports by using the BizTalk Server Administration console. The orchestration uses these ports to pick messages that an adapter client sends. The orchestration then passes the messages to the SAP system. Once a response is received from the SAP system, the orchestration passes the response to the adapter client.  
  
- **Create messages and link to schema**. In your orchestration, you must create messages that will be mapped to the schema you generated in the first step. Typically, you create a request message and a response message. These messages are mapped to corresponding request and response schemas.  
  
- **Map message shapes to messages and ports**. In your orchestration, you must now map each shape you added in the second step to messages you created in the third step. You must also map a message shape to the port on which that message will be sent.  
  
   For example, if the first shape in your orchestration is a Receive shape that receives a message, you map this shape to a request message and the port that sends the request message.  
  
- **Build and deploy the BizTalk project**. After you have set up the orchestration and mapped messages, ports, and schemas you must build the BizTalk solution. For building a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you will need an assembly key file. After you successfully build the solution, you must deploy the solution.  
  
  > [!NOTE]
  >  More detailed description of these high-level tasks, including procedural information, is provided in various topics of this section.  
  
  Once the solution is deployed, your design-time tasks are accomplished. You must now perform the run-time tasks.  
  
## Run-time Tasks  
 At run time, you can use the BizTalk Server Administration console to deploy and monitor the orchestration you created at design time. In addition, you must:  
  
- **Configure the application**. The BizTalk project you deployed at design time shows up in the BizTalk Server Administration console as an orchestration. You must configure this orchestration by mapping the logical ports you created at design time to physical ports that you must now create using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
   On the physical ports, you must specify an "action" or "action mapping". This action corresponds to the operation you want to perform on the SAP system. You need to set the action if you are not using dynamic actions. 
  
- **Start the application**. After the application is configured, you must start the application, and drop input messages at a defined file location. The orchestration consumes the input messages and passes them to the SAP system and receives a response. This response will be available to you at another defined file location.  
  
  To accomplish these high-level design-time and run-time tasks, you must also perform other tasks. For example, when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema, you must specify a connection URI to connect to the SAP system. This section provides information on such repetitive tasks that you must perform as you develop BizTalk applications using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## In This Section  
  
-   [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)  
  
-   [Configure the connection URI for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md)  
  
-   [Configure the sign in credentials for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md) 
  
-   [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)
  
-   [Configure the SOAP action for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)
  
-   [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)
  
-   [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)
  
-   [Configure dynamic ports in the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md)
  
-   [Reuse SAP adapter bindings](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)
  
## See Also  
[Develop BizTalk applications using the SAP adapter](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)