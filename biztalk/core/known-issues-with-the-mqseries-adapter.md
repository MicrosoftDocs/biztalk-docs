---
description: "Learn more about: Known Issues with the MQSeries Adapter"
title: "Known Issues with the MQSeries Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c36bcabb-e1eb-455c-8384-00d4682464d3
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the MQSeries Adapter
This section contains information that may help you avoid errors.

## Know Issues

#### Access Denied errors occur when attempting to send or receive messages

##### Problem
 When you use the MQSeries adapter to send messages to or receive messages from an MQSeries server, error messages that are similar to the following are logged in the Application log in Event Viewer:

```
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."
```

```
The adapter failed to transmit message going to send port "MQS://servername/queuename". It will be retransmitted after the retry interval specified for this Send Port. Details: "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."
```

> [!NOTE]
>  In this error message, *servername* is the name of the server and *queuename* is the name of the queue.

 Additionally, when you try to create the receive location or the send port that is configured to use the BizTalk Adapter for MQSeries, you may receive the following warning message in Event Viewer:

```
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."
```

##### Cause
 This issue may occur if one or more of the following conditions are true:

- The host account for the MQSeries adapter does not have the required permissions for the MQSAgent COM+ application on the MQSeries server.

- On a Windows server, the host account for the MQSeries adapter is not a member of the Distributed COM Users group on the MQSeries server.

##### Resolution
 To resolve this issue, use the following methods. If a method does not resolve the issue, try the next method.

 **Method 1: Enable network COM+ access on the Microsoft Server**

 Enable network COM+ access on the Microsoft Server. For more information, go to [enable COM+ Network Access](/troubleshoot/windows-server/application-management/0x80004027-remotely-access-com-plus-object).

 **Method 2: Configure MSDTC settings**

 Follow the steps in the **Set the appropriate MSDTC Security Configuration options** at [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) to configure MSDTC settings.

 **Method 3: Verify that the host account is added to the role in the MQSAgent COM+ application**

 Verify that the host account for the MQSeries adapter is added to the role that was created in the MQSAgent COM+ application on the MQSeries server. You can verify this in the Component Services management console interface.

 **Method 4: Verify that the host account for the MQSeries adapter is a member of the Distributed COM Users group**

 On a Windows Server, examine the group memberships of the host account for the MQSeries adapter. Make sure that the account is a member of the **Distributed COM Users** group on the MQSeries server where the MQSAgent COM+ application is installed.

 For more information about DCOM security enhancements, see [DCOM Security Enhancements](/previous-versions/windows/it-pro/windows-server-2003/cc738214(v=ws.10)).

## See Also
 [Troubleshooting the MQSeries Adapter](../core/troubleshooting-the-mqseries-adapter.md)