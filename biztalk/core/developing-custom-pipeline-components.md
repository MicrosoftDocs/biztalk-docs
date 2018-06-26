---
title: "Developing Custom Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom]"
  - "pipeline components [custom], about pipeline components"
  - "pipeline components [custom], creating"
  - "customizing, pipeline components"
  - "pipeline interfaces"
  - "IDisassemblerComponent"
  - "pipeline interfaces, about pipeline interfaces"
  - "creating, pipeline components [custom]"
  - "IAssemblerComponent"
  - "IComponent"
  - "pipeline components [custom], customizing"
  - "pipeline interfaces, interface types"
  - "pipeline components [custom], interfaces"
  - "pipeline components [custom], component types"
ms.assetid: cce61e0d-f1e3-4ec2-b38c-7c6eaf83ac10
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing Custom Pipeline Components
This section describes how to develop a pipeline component. You can create three types of pipeline components: general, assembling, and disassembling. Each of the three types can additionally implement probing functionality. Each type of pipeline component has an associated interface that must be implemented for the component to be plugged into the BizTalk Messaging Engine; the pipeline interfaces that distinguish the types of components are **IComponent**, **IAssemblerComponent**, and **IDisassemblerComponent**. For probing components, you must implement the **IProbeMessage** interface.  
  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a sample pipeline component that you can reference when creating your own component. The sample component demonstrates how to append data to the end of a message and add data at the beginning of the message. For more information about the sample pipeline component, see [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md).  
  
> [!CAUTION]
>  If you reference a custom pipeline component from a pipeline in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], a compile-time error may occur. To correct the error, close Pipeline Designer and reopen it before compiling. Alternatively, you can remove the component, and then add it.  
> 
> [!IMPORTANT]
>  When upgrading to BizTalk Server, ensure that any string variables in your existing custom pipeline components do not contain any newline characters such as ‘\n’. Otherwise, a “newline in constant” error will occur when compiling this component in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## In This Section  
  
-   [Using Pipeline Interfaces](../core/using-pipeline-interfaces.md)  
  
-   [Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md)  
  
-   [Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md)  
  
-   [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md)  
  
-   [Implementing a Seek Method in a Managed Streaming Pipeline Component](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [Using the Parsing and Serializing Engines](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md)  
  
-   [Deploying Pipeline Components](../core/deploying-pipeline-components.md)  
  
-   [Debugging Custom Pipelines](../core/debugging-custom-pipelines.md)