---
description: "Learn more about: How to Use MessageBox Direct Bound Ports"
title: "How to Use MessageBox Direct Bound Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1839184b-408e-4ac6-94a4-a0eb708183f6
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use MessageBox Direct Bound Ports
MessageBox direct bound ports enable you to drop messages directly into the MessageBox database without an explicit recipient, and to subscribe to messages that meet certain criteria rather than messages that come from a particular sender.

 Sending a message on a MessageBox direct bound port is equivalent to publishing the message to a message bus—in this case, to the MessageBox database. There can be any number of subscribers for any published message, and if there are no subscribers interested in the message at the time you publish it, a "subscription not found" exception will be thrown. If you send a message through a MessageBox direct bound port with a particular recipient in mind, you may want to set properties to particular values in the **Message Assignment** shape for your intended subscriber to look for. You can set the properties based on BizTalk Server predefined property definitions or on your own property definitions. For example:

```
myMessage(PropertyNamespace.PropertyName) = "My Property")
```

 Receiving a message through a MessageBox direct bound port is equivalent to subscribing to a message bus with filter criteria. Recipients of the message can be any type of service that can subscribe to messages, which includes orchestrations and send ports. For an activating **Receive** shape the subscription is the message type and the filter expression, and for a non-activating **Receive** shape the subscription is the message type and the correlation set. Every **Receive** shape always includes the message type as part of its subscription.

> [!NOTE]
>  You must use a filter expression if you have an activating **Receive** shape receiving a message of type **System.Xml.XmlDocument** or **Microsoft.XLANGs.BaseTypes.Any** on a direct bound port with subscription-defined routing.

 If you did not specify any filter criteria in the activating **Receive** shape connected to a MessageBox direct bound port, then the subscription will look similar to the following:

```
http://schemas.microsoft.com/BizTalk/2003/system-properties.ReceivePortID == {2F6A80E1-2518-4A69-9C28-401C2DB1CBF6} And
http://schemas.microsoft.com/BizTalk/2003/system-properties.MessageType == http://MyMessageType
```

 In the preceding example, the MessageBox direct bound receive port will receive every message that matches the message type that the port’s operation is configured for.

> [!NOTE]
>  When using MessageBox direct bound receive ports, you should make the filter as specific as possible. If you do not make the filter specific enough, your orchestration may receive unwanted messages.

 To configure a MessageBox direct bound port, select **Routing between ports will be defined by filter expressions on incoming messages in the Message Box database** in the Port Configuration Wizard.

 For an example of how to use MessageBox direct bound ports, see the SDK sample "Direct Binding to the MessageBox Database in Orchestrations" at [https://go.microsoft.com/fwlink/?LinkId=73703](https://go.microsoft.com/fwlink/?LinkId=73703).

## See Also
 [How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md)
 [How to Use Partner Orchestration Direct Bound Ports](../core/how-to-use-partner-orchestration-direct-bound-ports.md)
