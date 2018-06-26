---
title: "How to Use Partner Orchestration Direct Bound Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19f9987f-79fb-4cb6-bf6e-542f6eea9ce0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use Partner Orchestration Direct Bound Ports
Partner orchestration direct bound ports provide the capability of having inter-orchestration communication through ports. You can create two communication patterns: forward partner orchestration direct binding and inverse partner orchestration direct binding. These two patterns provide explicit inter-orchestration communication, which means that there is an intended recipient orchestration when using forward partner orchestration direct binding and an intended sender orchestration when using inverse partner orchestration direct binding.  
  
 You can also design implicit partner orchestration direct binding by doing one of the following:  
  
- Make the receiver a MessageBox direct bound port and create a filter that will accept messages from a particular sending orchestration.  
  
- Make the sender a MessageBox direct bound port and promote properties that will match a subscription on the receiving orchestration.  
  
  To configure a partner orchestration direct bound port, in the Port Configuration Wizard, specify **Direct** for **Port binding** and select **To receive messages from other orchestrations, select this port here and in those orchestration** or **To send messages to other orchestrations, select this port here and in those orchestration** depending on whether you are receiving or sending messages on this port. Then select the port from the **Port on partner orchestration** drop-down list. The port type for both ports must be the same, which implies that the message type must also be the same. Moreover, to be able to direct bind to a partner orchestration port, the **Type Modifier** of the port type must be either **Internal** for orchestrations within the same assembly or **Public** to allow an orchestration from another assembly to bind to it. The polarities of the ports must be opposite. For example, if one side is a send port then the other side must be a receive port.  
  
  For an example of how to use partner orchestration direct bound ports, see the SDK sample "Direct Binding to an Orchestration" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## Forward Partner Orchestration Direct Binding  
 This is the typical communication pattern that is used for partner orchestration direct binding. This type of forward partner orchestration binding allows you to have multiple senders bound to the same recipient.  
  
 **To configure forward partner orchestration direct binding, do the following:**  
  
1. In Orchestration A, select the **Port** shape in the orchestration Toolbox. This starts the Port Configuration Wizard.  
  
2. On the **Port Properties** page, in the **Name** field, type `MyReceivePort`. Click **Next**.  
  
3. On the **Select a Port Type** page, select **Create a new Port Type**. In the **Port Type Name** field, type `MyPartnerPortType`. Click **Next**.  
  
4. On the **Port Binding** page, in the **Port direction of communication** drop-down list, select **I'll always be receiving messages on this port**. In the **Port binding** drop-down list, select **Direct**.  
  
5. Select **To receive messages from other orchestrations, select this port here and in those orchestrations**, and then in the **Port on partner orchestration** drop-down list, select **OrchestrationA.MyReceivePort**. Click **Next**.  
  
6. On the **Completing the Port Wizard** page, click **Finish**.  
  
7. In Orchestration B, select the **Port** shape in the orchestration Toolbox. This starts the Port Configuration Wizard.  
  
8. On the **Port Properties** page, in the **Name** field, type `MySendPort`. Click **Next**.  
  
9. On the **Select a Port Type** page, select **Use an existing Port Type**. Under **Available Port Types**, select **MyPartnerPortType**, and then click **Next**.  
  
10. On the **Port Binding** page, in the **Port direction of communication** drop-down list, select **I'll always be sending messages on this port**. In the **Port binding** drop-down list, select **Direct**.  
  
11. Select **To send messages to other orchestrations, select this port here and in those orchestrations**, and then in the **Port on partner orchestration** drop-down list, select **OrchestrationA.MyReceivePort**. Click **Next**.  
  
12. On the **Completing the Port Wizard** page, click **Finish**.  
  
    > [!NOTE]
    >  There is a strong binding from the sender orchestration to the receiver orchestration. Therefore, if you want to modify the receiver orchestration or if you want to change the version of the receiver orchestration, you must update the design-time configuration of the sender partner orchestration direct bound port. However, because the receiver orchestration has no explicit knowledge of the sender orchestration, you can update the sender orchestration without affecting the receiver orchestration.  
  
    In the preceding configuration, Orchestration A is the recipient and Orchestration B is the sender. The configuration enables Orchestration B to send messages to **OrchestrationA.MyReceivePort**, and enables Orchestration A to receive any messages sent to **OrchestrationA.MyReceivePort**. Moreover, you can add Orchestration C to be the second sender and add Orchestration D to be the third sender by using the same configuration as for Orchestration B.  
  
## Inverse Partner Orchestration Direct Binding  
 This is not the typical communication pattern that is used for partner orchestration direct binding. In this pattern the direction of binding is the reverse of the direction of communication. This type of inverse partner orchestration binding allows you to have a single sender communicate with multiple receivers.  
  
> [!NOTE]
>  If you are using a two-way port type with inverse partner orchestration direct binding, then you must set up your receiving filters to ensure that only one of the recipients will consume the message. This is because a solicit-response port is expecting a single response. If multiple recipients get the message, then the solicit-response port accepts the first response and all subsequent responses are suspended and non-resumable. The messaging engine throws an exception when you try to send the message under this situation, and indicates that there are multiple recipients for a solicit-response port.  
  
 **To configure inverse partner orchestration direct binding, do the following:**  
  
1. In Orchestration A, select the **Port** shape in the orchestration Toolbox. This starts the Port Configuration Wizard.  
  
2. On the **Port Properties** page, in the **Name** field, type `MySendPort`. Click **Next**.  
  
3. On the **Select a Port Type** page, select **Create a new Port Type**. In the **Port Type Name** field, type `MyPartnerPortType`. Click **Next**.  
  
4. On the **Port Binding** page, in the **Port direction of communication** drop-down list, select **I'll always be sending messages on this port**. In the **Port binding** drop-down list, select **Direct**.  
  
5. Select **To send messages to other orchestrations, select this port here and in those orchestrations**, and then in the **Port on partner orchestration** drop-down list, select **OrchestrationA.MySendPort**. Click **Next**.  
  
6. On the **Completing the Port Wizard** page, click **Finish**.  
  
7. In Orchestration B, select the **Port** shape in the orchestration Toolbox. This starts the Port Configuration Wizard.  
  
8. On the **Port Properties** page, in the **Name** field, enter `MyReceivePort`. Click **Next**.  
  
9. On the **Select a Port Type** page, select **Use an existing Port Type**. Under **Available Port Types**, select **MyPartnerPortType**, and then click **Next**.  
  
10. On the **Port Binding** page, in the **Port direction of communication** drop-down list, select **I'll always be receiving messages on this port**. In the **Port binding** drop-down list, select **Direct**.  
  
11. Select **To receive messages from other orchestrations, select this port here and in those orchestrations**, and then in the **Port on partner orchestration** drop-down list, select **OrchestrationA.MySendPort**. Click **Next**.  
  
12. On the **Completing the Port Wizard** page, click **Finish**.  
  
    > [!NOTE]
    >  The receiver orchestration is strongly bound to the sender orchestration. Therefore, if you want to modify the receiver orchestration or update the version of the receiver orchestration, you must update the sender’s port configuration. The sender orchestration has no explicit knowledge of the receiver orchestration, so you can update the receiver orchestration without affecting the sender orchestration.  
  
    In the preceding configuration, Orchestration A is the sender and Orchestration B is the recipient. The configuration enables Orchestration A to send messages to Orchestration B through **OrchestrationA.MySendPort**, and enables Orchestration B to receive messages from **OrchestrationA.MySendPort**. Moreover, you can add Orchestration C to be the second recipient and add Orchestration D to be the third recipient by using the same configuration as for Orchestration B.  
  
## See Also  
 [How to Use MessageBox Direct Bound Ports](../core/how-to-use-messagebox-direct-bound-ports.md)   
 [How to Use Self-Correlating Direct Bound Ports](../core/how-to-use-self-correlating-direct-bound-ports.md)