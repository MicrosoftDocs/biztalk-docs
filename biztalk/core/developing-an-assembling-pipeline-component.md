---
title: "Developing an Assembling Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IComponentUI interface, assembling"
  - "IBaseComponent interface, assembling"
  - "pipeline interfaces, IBaseComponent"
  - "pipeline components [custom], interfaces"
  - "pipeline interfaces, IComponentUI"
  - "IAssemblerComponent interface, assembling"
  - "pipeline interfaces, IAssemblerComponent"
  - "pipeline components [custom], assembling"
ms.assetid: 2f85421d-2010-4a36-82b5-ea8016f8aa99
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing an Assembling Pipeline Component
An assembling pipeline component is a .NET or COM component that receives several messages on input and produces one message on output. Assembling components are used to collect individual documents into the message interchange batch.  
  
> [!NOTE]
>  Assembly functionality is not used, so BizTalk Server always passes one document to the component input.  
  
 An assembling component must implement the following interfaces:  
  
-   `IBaseComponent`  
  
-   `IAssemblerComponent`
  
-   `IComponentUI`
  
-   **IPersistPropertyBag .** Refer to the .NET Framework SDK documentation for this interface.  
  
> [!NOTE]
>  Custom pipeline components should copy any additional parts from the input message to the output message(s). This preserves them for further processing in the pipeline.  
  
## See Also  
 [Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md)   
 [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md)   
 [Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md)   
 [Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Deploying Pipeline Components](../core/deploying-pipeline-components.md)   
 [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md)