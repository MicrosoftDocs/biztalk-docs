---
title: "Receiving from PeopleSoft | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9acc71ec-05b8-4490-b3ba-0ce7f27a5a6a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receiving from PeopleSoft
The Microsoft Adapter for PeopleSoft Enterprise is a send adapter. The adapter supports solicit-response, so that you can send a query and get back a response. However, if you want only to receive data from PeopleSoft, you must take two additional steps:  
  
1.  Create a custom receive pipeline using the Set Namespace pipeline component.  
  
2.  Create a receive port accessible from PeopleSoft such as a port using the HTTP Adapter. Use the custom receive pipeline with the receive port.  
  
## The Set Namespace Pipeline Component  
 Messages received from PeopleSoft do not include namespaces. The Set Namespace pipeline component enables you to add a namespace to the incoming message.  
  
 The default location for the Set Namespace pipeline component is C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component. You need to copy the component, Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll, to the Pipeline Component directory used by BizTalk. You also need to add the component to the Visual Studio Toolbox in order to use it in the Pipeline Designer.  
  
 For information about where to install the component, see [Deploying Pipeline Components](../core/deploying-pipeline-components.md).  
  
 For information about adding the component to the Visual Studio Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).  
  
## Configuring the Set Namespace Pipeline Component  
 The Set Namespace pipeline component has two properties you can set:  
  
|Use this|To do this|  
|--------------|----------------|  
|**Default Target Namespace**|Put a fixed namespace in the incoming message.|  
|**Target Namespace XPath**|Extract the namespace from the incoming message taking it from the location specified by the XPath. If the component does not find a valid namespace, it logs a warning in the Application Event Log and, if it is specified, uses the Default Target Namespace.|  
  
 If you leave both properties blank, the component does not assign namespaces to incoming messages but does write warnings to the Application Event Log.  
  
## See Also  
 [Developing Applications](../core/developing-applications4.md)