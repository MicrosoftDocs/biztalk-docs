---
title: "Developing a General Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63f5d8d1-30fb-4a1e-b4bd-2be07b618b20
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Developing a General Pipeline Component

## Interfaces
A general pipeline component is a .NET or COM component that implements the following interfaces:  
  
- IBaseComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- IComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- IComponentUI Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
- [IPersistPropertyBag](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
  A general pipeline component gets one message from the BizTalk Messaging Engine, processes it, and returns it to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine. General components can also be implemented so that they do not return messages to the server. Such components are called consuming components because the component receives messages but does not produce any result messages.  
  
> [!NOTE]
>  Custom pipeline components should copy any additional parts from the input message to the output message(s). This preserves them for further processing in the pipeline.  
  
## More pipeline resources
 [Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md)   
 [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md)   
 [Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md)   
 [Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Deploying Pipeline Components](../core/deploying-pipeline-components.md)   
 [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md)