---
description: "Learn more about: MSMQ Adapter Architecture"
title: "MSMQ Adapter Architecture"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MSMQ Adapter Architecture
The MSMQ adapter lets you take advantage of Microsoft Message Queuing (also known as MSMQ) features that are otherwise unavailable in BizTalk Server.

## Adapter Structure
 The MSMQ adapter has the same structure as other BizTalk adapters and uses the Adapter Framework. It is made up of a design-time component and a run-time component. The run-time component, in turn, contains the elements that implement the message transport.

 The design-time component lets you configure the adapter properties for sending and receiving.

 The run-time component can send messages to a queue defined at design time or receive messages from a designated queue. The adapter runtime runs in the same process as the BizTalk Server application and does not run in an isolated host.

 All message handling relies on the local Message Queuing service, even for remote queues. For remote queues, the adapter hands messages off to the local Message Queuing service. It, in turn, sends the messages to the remote queue.

 For a complete list of send and receive configuration properties, see [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md) and [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md).

 For more information about Message Queuing, see the following topics available in the Microsoft TechNet Library:

-   **Message Queuing Design Guide** at [https://go.microsoft.com/fwlink/?LinkId=137080](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731344(v=ws.10)).

-   **Message Queuing Operations Guide** at [https://go.microsoft.com/fwlink/?LinkId=137079](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731022(v=ws.10)).

-   **Message Queuing Troubleshooting Guide** at [https://go.microsoft.com/fwlink/?LinkId=137081](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730982(v=ws.10)).

-   **Message Queuing Technical Reference** at [https://go.microsoft.com/fwlink/?LinkId=137082](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753070(v=ws.10)).

## See Also
 [What Is the MSMQ Adapter?](../core/what-is-the-msmq-adapter.md)