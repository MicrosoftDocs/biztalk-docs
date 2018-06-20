---
title: "The ESB Dispatcher Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85655b5f-4717-42d1-b005-0a5592d5653b
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The ESB Dispatcher Component
Messaging-based itinerary services are executed inside the ESB Dispatcher component. The Dispatcher component can also dynamically set endpoint location properties for outbound messages and dynamically transform messages.  
  
## Component Properties  
 The Dispatcher component has six properties:  
  
- **RoutingServiceName**. This property specifies the registered name for the messaging-based routing service. The default value is **Microsoft.Practices.ESB.Services.Routing**.  
  
- **TransformServiceName**. This property specifies the registered name for the messaging-based transform service. The default value is **Microsoft.Practices.ESB.Services.Transform**.  
  
- **Validate**. This property specifies whether a message needs to be validated.  
  
- **Enabled**. This property enables or disables the component.  
  
- **Endpoint**. This property is a resolver connection string in a format registered with BizTalk ESB Toolkit.  
  
- **Map Name**. This property is either the fully qualified name of a map or a connection string format registered with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
  -   The following is an example of a map name:  
  
      ```  
      GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN, GlobalBank.ESB.DynamicResolution.Transforms, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a  
      ```