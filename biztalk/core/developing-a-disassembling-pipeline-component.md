---
description: "Learn more about: Developing a Disassembling Pipeline Component"
title: "Developing a Disassembling Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Developing a Disassembling Pipeline Component
A disassembling pipeline component receives one message on input and produces zero or more messages on output. Disassembling components are used to split interchanges of messages into individual documents. Disassembler components must implement the following interfaces:  
  
- `IBaseComponent`
  
- `IDisassemblerComponent`
  
- `IComponentUI`
  
- **IPersistPropertyBag .** Refer to the .NET Framework SDK documentation for this interface.  
  
  You can create your own disassembling component by extending the **FFDasmComp** or **XMLDasmComp** class.  
  
> [!WARNING]
>  If your custom disassembler will be setting the MessageDestination context property to SuspendQueue, the stream returned by the disassembler must to support Seek(0) for the suspension to work.  
  
> [!NOTE]
>  Custom pipeline components should copy any additional parts from the input message to the output message(s). This preserves them for further processing in the pipeline.  
  
## In This Section  
  
-   [Handling Incoming Data Streams in Pipeline Components](../core/handling-incoming-data-streams-in-pipeline-components.md)  
  
-   [Handling Encoding in a Disassembler Pipeline Component](../core/handling-encoding-in-a-disassembler-pipeline-component.md)  
  
-   [Extending the Flat File Disassembler Pipeline Component](../core/extending-the-flat-file-disassembler-pipeline-component.md)
