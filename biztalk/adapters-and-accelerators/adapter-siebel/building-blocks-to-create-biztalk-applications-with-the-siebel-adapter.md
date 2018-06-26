---
title: "Building blocks to create BizTalk applications with the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "developing BizTalk applicatons, run-time tasks"
  - "developing BizTalk applications, design-time tasks"
ms.assetid: 76204181-18ad-43b5-b589-539aafd66835
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Building blocks to create BizTalk applications with the Siebel adapter
Performing operations on a Siebel system using [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] involves two set of activities: design-time activities and run-time activities. To perform operations on a Siebel system by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must perform a set of design-time and run-time tasks using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console respectively. This section provides an overview of these tasks. All the topics in this section, which demonstrate how to perform specific operations on a Siebel system using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], are modeled on these high-level tasks.  
  
## Design-time tasks  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides capability to browse, search, and retrieve the Siebel metadata for business components and business services in the form of XML Schema definition languages (XSDs) using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. The XSDs are specific to the operation you wish to perform on the Siebel system and the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] is available only when you create a BizTalk Project. At design time you may need to perform the following tasks.  
  
- **Create BizTalk project and generate schema**. To start with, you must create a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and generate the schema for the business components or the business services you will invoke in the Siebel system. For example, if you want to insert a record into the Account business component, you must generate the metadata for the Insert operation for the Account business component. In this step you use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema. For more information, see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
- **Set up an orchestration**. Once you have generated the schema, you must set up an orchestration by using the Orchestration Designer. For a basic orchestration, you add the Send and Receive shapes along with the Send and Receive logical ports. In the later steps, you will map these logical ports to physical ports by using the BizTalk Server Administration console. The orchestration uses these ports to pick up messages sent by an adapter client. The orchestration then passes the messages to the Siebel system. Once a response is received from the Siebel system, the orchestration passes the response to the adapter client.  
  
- **Create messages and link to schema**. In your orchestration, you must create messages that will be mapped to the schema you generated in the first step. Typically, you would create a request and a response message. These messages are mapped to corresponding request and response schemas.  
  
- **Map message shapes to messages and ports**. In your orchestration, you must now map each shape you added in the second step to messages you created in the third step. You must also map a message shape to the port on which that message will be sent.  
  
   For example, if the first shape in your orchestration is a Receive shape that will receive a message, you will map this shape to a "request" message and the port that sends the request message.  
  
- **Build and deploy the BizTalk project**. After you have set up the orchestration and mapped messages, ports, and schemas you must build the BizTalk solution. For building a project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you will need an assembly key file. After you successfully build the solution, you must deploy the solution.  
  
  > [!NOTE]
  >  More detailed description of these high level tasks, including procedural information is provided under the topics that follow.  
  
  Once the solution is deployed, your design time tasks are accomplished. You must now perform the run time tasks.  
  
## Run-time tasks  
  
- **Configure the application**. The BizTalk project you deployed at design time will show up in the BizTalk Server Administration console as an orchestration. You must configure this orchestration by mapping the logical ports you created at design time to physical ports that you must now create using the BizTalk Server Administration console.  
  
   On the physical ports, you must specify an "action" or "action mapping". This action corresponds to the operation you want to perform on the Siebel system. You need to set the action if you are not using dynamic actions. 
  
- **Start the application**. After the application is configured, you must start the application, and drop input messages at a defined file location. The orchestration consumes the input messages and passes them to the Siebel system and receives a response. This response will be available to you at another defined file location.  
  
  To accomplish these high-level design-time and run-time tasks, you must also perform other tasks. For example, when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate the schema, you must specify a connection URI to connect to the Siebel system. This section provides information on such repetitive tasks that you must perform as you develop BizTalk applications by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
