---
title: "Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations"
  - "correlations, orchestrations"
  - "orchestrations, correlations"
  - "orchestrations, deploying"
  - "deploying, orchestrations"
  - "orchestrations, about orchestrations"
ms.assetid: fb01f78a-b805-46be-a7d9-2b7597daab96
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestrations
*Orchestrations* are executable business processes that can subscribe to (receive) and publish (send) messages through the MessageBox database. In addition, orchestrations can construct new messages. Messages are received using the subscription and routing infrastructure discussed in [Lifecycle of a Message](../core/lifecycle-of-a-message.md). When subscriptions are filled for orchestrations, a new instance is activated and the message is delivered, or in the case of instance subscriptions, the instance is rehydrated if necessary and the message is then delivered. When messages are sent from an orchestration, they are published to the MessageBox in the same manner as a message arriving on a receive location with the appropriate properties getting inserted into the database for use in routing.  
  
 Messages that are constructed in an orchestration must be placed in the MessageBox database and referenced by the orchestration instance, but they should not be published because they have not yet been sent. The XLANG/s subservice makes calls to the Message Agent API to insert messages directly. This allows the orchestration engine to insert the message body into the MessageBox and have it directly associated with the running orchestration instance. The persistence of the constructed message in the MessageBox database is coordinated with persistence points in the orchestration as an additional optimization of database operations.  
  
 The concept in orchestrations that makes the publish and subscribe seem to act differently is binding. Orchestration ports are logical ports that describe an interaction. You must bind these logical ports to a physical port so that messages are delivered, but this binding process is nothing more than configuring subscriptions for message routing.  
  
 There are four basic options for binding these ports:  
  
-   Specify Now (specifying ports directly in the orchestration)  
  
-   Specify Later (specifying ports at deployment time)  
  
-   Using a dynamic send port where the address is set in the orchestration code  
  
-   Creating a direct binding from the orchestration to either the MessageBox database or to another orchestration  
  
## Deploying Orchestrations  
 When a binding is specified at design time, the physical port that matches the parameters configured in the orchestration is created when the orchestration is deployed. When the binding is configured at deployment time, any port that matches the requirements of the logical port can be bound to the orchestration port. For dynamic binding, a physical port is created just as with the Specify Now option, but the port is a dynamic send port that has no address information configured.  
  
 A confusing concept is that while a send port in an orchestration is bound to a physical send port, this does not preclude that message from getting delivered to other subscribers. That is, if another send port happens to have a subscription, through its filters, for the message being sent to the bound port, both send ports receive the message. Binding simply creates the subscription such that the message sent from the orchestration always matches the criteria for the bound send port. Likewise, the orchestration port bound to a receive port creates the appropriate subscription based on message type and receive port ID. The subscriptions guarantee that the messages going in and out of the orchestration get delivered to the bound ports, but the messages still go through the same publish and subscribe mechanism described earlier.  
  
 Probably the most misunderstood, and misused or underused binding option is the Direct binding option. Direct binding allows an orchestration to publish messages to the MessageBox database with varying routing properties much like messages are published by receive locations. In simple direct messaging, the message is published to the MessageBox with its promoted properties to be routed like any other published message received into BizTalk Server. This enables any subscriber to receive this message, but requires that at least one subscriber exist or the orchestration will receive a routing failure error.  
  
 Another option for direct binding is to use self-correlating ports. Self-correlating ports are ports that create a unique correlation token and use that token alone in correlating messages between instances. The most common use of a self-correlating port is to call or start an orchestration passing in a port parameter. In the called orchestration, the port can be used to send a message, while in the calling orchestration the same port can be used to receive a message. Because the port has a unique correlation token, the message is routed back to the calling orchestration. Self-correlation ports act as private communication channels between orchestration instances.  
  
 The final option is to use a partner orchestration in which, in both the calling orchestration and the called orchestration, the port is configured using the same shared port type and in the port configuration, the same port is selected. For example, in both Orch1 and Orch2, Orch2.MyDirectPort is selected. This type of binding sets up a subscription for the receiving orchestration based on the sending orchestration type, the port name, and the operation name. This again ensures that the messages get routed to the correct instance.  
  
 All of the direct messaging options use the underlying publish and subscribe model. The difference between these options is in the properties that are used for creating subscriptions and routing, and in the use cases they help solve.  
  
 One common problem encountered when using direct bound ports in orchestrations is that an orchestration may publish a message that it is also subscribed to. For example, an orchestration is configured to be activated by a PurchaseOrder message. This orchestration uses a direct port to publish the PurchaseOrder message to the MessageBox. However, in addition to receiving the message as expected, another instance of an orchestration is started because it too had a subscription for PurchaseOrder messages. The processing gets into an endless loop and it may take some time for a developer to figure out what has happened.  
  
## Correlation  
 *Correlation* in orchestrations is the mechanism for receiving related messages into the same running orchestration instance. In the Orchestration Designer a developer follows these general steps to use a correlation:  
  
- Defines a correlation type that includes the promoted properties that are used to relate messages.  
  
- Defines a correlation set that is an instance of the correlation type just defined.  
  
- For the send and receive ports, specifies whether they initiate or follow a given correlation set.  
  
  Instance subscriptions come into play when a correlation set is initiated, as this is when subscriptions are created for all of those ports that follow this correlation set to receive messages. Because the correlation type defines the properties to be used for correlation, the orchestration engine can extract these properties from the message being sent or received by the initiating action. These values are then used to define subscriptions for all of the remaining actions which follow this correlation set.  
  
  It is important that messages received into BizTalk Server and intended for use in a correlation have their promoted properties correctly defined and promoted to the message context. Most properties get promoted when a disassembler component in a pipeline extracts the values when the message is initially received. For this reason, it is not possible to use the PassThrough receive pipeline to receive messages that must be correlated to a running instance of an orchestration. This issue arises when you use the SOAP receive adapter to receive correlated messages, because the PassThrough pipeline is the default value for the receive pipeline when using the Web Services Publishing Wizard.  
  
## See Also  
 [Artifacts](../core/artifacts.md)   
 [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md)