---
title: "Port Bindings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, warnings"
  - "ports, bindings"
  - "bindings, Web ports"
  - "bindings, design time"
  - "Web ports, port bindings"
  - "bindings, ports"
  - "bindings, direct"
  - "bindings, warnings"
  - "bindings, deployment"
  - "bindings, dynamic"
ms.assetid: b61c725a-0082-42d3-b88a-533583161734
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Port Bindings
A port binding is the configuration information that determines where and how a message will be sent or received. Depending on its type, a port binding might refer to physical locations, pipelines, or other orchestrations.  
  
 There are three types of port binding for ports that receive messages:  
  
- Specify now  
  
- Specify later  
  
- Direct  
  
  There are four types of port binding for ports that send messages:  
  
- Specify now  
  
- Specify later  
  
- Direct  
  
- Dynamic  
  
## Binding at Deployment Time  
 You can bind your port to a receive location or to a send port. If you do not have all of the information you need to specify a physical location, you can select the **Specify later** port binding option in Orchestration Designer, and you only need to specify the port type that describes the port. After the application has been deployed, you can specify information about the location by using the BizTalk Server Administration console, or you can configure the location information programmatically.  
  
## Binding at Design Time  
 You can select the **Specify now** port binding option in Orchestration Designer to specify the transport and pipeline at design time. When specifying the port for receiving messages, only HTTP, SOAP, and FILE transports are available from the drop-down list. When specifying the port for sending messages, only HTTP, FILE, and SMTP transports are available from the drop-down list. This option is useful if you know in advance the source or destination of transmitted messages.  
  
## Direct Binding  
 Direct bound ports are logical one-way or two-way ports in your orchestrations that are not explicitly bound to any physical ports. Direct bound ports allow you to have different communication patterns among your services. To implement direct binding, select the **Direct** port binding option in Orchestration Designer at design time.  
  
 There are three types of direct bound ports:  
  
- MessageBox direct bound port  
  
- Self-correlating direct bound port  
  
- Partner orchestration direct bound port  
  
  For more information about how to work with direct bound ports, see [Working with Direct Bound Ports in Orchestrations](../core/working-with-direct-bound-ports-in-orchestrations.md).  
  
> [!NOTE]
>  When you use direct binding, you cannot exchange messages between one request-response port and two one-way ports.  
  
> [!NOTE]
>  Direct binding is not compliant with the standards of the Business Process Engineering Language for Web Services (BPEL4WS). If you require BPEL4WS compliance, use another kind of binding.  
  
## Dynamic Binding  
 If you will not know the destination of a communication until run time, you can use dynamic binding for a send port. The location might, for example, be determined from a property on an incoming message, and then specified in the **Expression** shape, as shown in the following code:  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
```  
  
 For information about how to dynamically assign values to ports, see [How to Assign Values to Dynamic Ports](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md).  
  
## Web Ports  
 If your project contains a reference to a Web service, Orchestration Designer will detect it and will make available a corresponding Web port type. To create a Web port, you simply add a port to your orchestration and assign it an existing Web port type. For more information, see [Creating Web Ports](../core/creating-web-ports.md).  
  
## See Also  
 [How to Work with Port Types](../core/how-to-work-with-port-types.md)   
 [Communication Pattern](../core/communication-pattern.md)   
 [Communication Direction](../core/communication-direction.md)   
 [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md)   
 [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)   
 [Consuming Web Services](../core/consuming-web-services.md)