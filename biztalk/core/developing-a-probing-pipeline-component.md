---
title: "Developing a Probing Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], probing"
  - "IProbeMessage interface"
  - "pipeline interfaces, IProbeMessage"
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing a Probing Pipeline Component
Any pipeline component (general, assembling, or disassembling) can implement the `IProbeMessage` interface if it must support message probing functionality. A probing component is used in the pipeline stages that have **FirstMatch** execution mode. In such stages, the BizTalk Messaging Engine gives the beginning part of the message to the component to determine if the component recognizes the format of the message. If the component recognizes the format, the entire message is given to the component for processing.  
  
 The **IProbeMessage** interface exposes a single method, **Probe**, which enables the component to check the beginning part of the message. The return value determines whether this component is run. The following steps outline how the BizTalk Messaging Engine runs a stage that requires recognition:  
  
1. If the stage does not contain any components, the stage is not run and the message is given to the subsequent stages for processing.  
  
2. Check if the component implements the **IProbeMessage** interface. If not, the Messaging Engine invokes the component. The stage processing is done and the message is given to the next stage.  
  
3. The **Probe** method is invoked. If the return value is **True**, the component is run. Then the stage processing is done and the message is given to a next stage.  
  
4. The Messaging Engine gets the next component in the stage. If there are no more components and none of the components have been run, it generates an error that pipeline processing has failed. If there are no more components and at least one component has been run, the processing is done.  
  
   If a stage does not require recognition (for example, the execution mode is **All**), the Messaging Engine invokes the component without first querying for the **IProbeMessage** interface and calling the **Probe** method.  
  
## See Also  
 [Developing a General Pipeline Component](../core/developing-a-general-pipeline-component.md)   
 [Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md)   
 [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md)   
 [Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Deploying Pipeline Components](../core/deploying-pipeline-components.md)