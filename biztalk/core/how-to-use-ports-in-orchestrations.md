---
description: "Learn more about: How to Use Ports in Orchestrations"
title: "How to Use Ports in Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use Ports in Orchestrations
You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form. You can also add ports by using the Orchestration View window.  
  
### To add a new port  
  
-   Right-click a **Port Surface** or a **Role Link**, and then click **New Port**.  
  
     —Or—  
  
     In the Orchestration View window, right-click **Ports** and then click **New Port**.  
  
     A DesignTip appears on ports that are not yet fully configured.  
  
    > [!TIP]
    >  You can also drag ports into a **Role Link**.  
  
### To add and configure a new port  
  
1.  From the **BizTalk Orchestrations** tab of the Toolbox, drag the **Port** shape onto a **Port Surface** or a **Role Link**.  
  
     —Or—  
  
     Right-click a **Port Surface** or a **Role Link**, and then click **New Configured Port**.  
  
     —Or—  
  
     In the Orchestration View window, right-click **Ports** and then click **New Configured Port**.  
  
     The Port Configuration Wizard appears.  
  
2.  Follow the steps in the wizard to configure the port. For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).  
  
### To remove a port  
  
-   Right-click the port to remove, and then click **Delete**.  
  
    > [!NOTE]
    >  If you delete a port after it has been connected to a **Send** or **Receive** shape in an orchestration that has been compiled, the port operations on the shape will not be deleted, and you will receive errors when you try to compile. Connect the shape to another port and reconfigure the port operations.  
  
### To configure a port by using the Port Configuration Wizard  
  
1.  Right-click the port to configure, and then click **Configure Port**.  
  
2.  Follow the steps in the Port Configuration Wizard to configure the port. For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).  
  
### To configure a port manually by using the Properties window  
  
1.  Select the port to configure.  
  
2.  In the Properties window, specify the following properties:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Port Type|Determines the communication pattern, operations, and multi-part message types associated with a port.|  
    |Communication Direction|Determines whether this orchestration is the sender or the receiver for this communication.|  
    |Communication Pattern|Determines if this port is used for request-response or one-way communication. (This property is determined by the **Port Type** property and is read-only.)|  
    |Binding|Determines how a message gets to its destination:<br /><br /> Direct—Communication is with another orchestration.<br /><br /> Dynamic—Communication is with an endpoint that is determined at run time.<br /><br /> Specify later—Communication is with an endpoint that is determined by an administrator at configuration time.<br /><br /> Specify now—Communication is with an endpoint that is known at design time.|  
    |Identifier|The name used for this port in the orchestration.|  
    |Ordered Delivery|For receive ports, ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order in which they were published to the message box. For more information, see [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md).|  
    |Delivery Notification|For send ports, determines whether want to receive an acknowledgment when a message is sent successfully. For more information, see "Delivery Notification" in [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md).|  
  
3.  The remaining properties to specify are determined by the **Binding** property:  
  
    -   Direct binding—Used when communicating directly with another orchestration.  
  
        |Property|Description|  
        |--------------|-----------------|  
        |Partner Orchestration Port|Determines to which port the partner orchestrations will be directly bound.|  
  
    -   Dynamic binding—Used when communicating with an endpoint that is determined at run time.  
  
        |Property|Description|  
        |--------------|-----------------|  
        |Receive Pipeline|Determines which pipeline to use for incoming messages.|  
        |Send Pipeline|Determines which pipeline to use for outgoing messages.|  
  
    -   Specify later—Used when communicating with an endpoint that is configured by an administrator.  
  
    -   Specify now—Used when communicating with an endpoint that is known at design time.  
  
        |Property|Description|  
        |--------------|-----------------|  
        |Receive Pipeline|Determines which pipeline to use for incoming messages.|  
        |Send Pipeline|Determines which pipeline to use for outgoing messages.|  
        |Transport|Determines which transport to use for sending messages.|  
        |URI|Determines where to send messages.|  
  
### To add a port operation  
  
-   Right-click the port to which you want to add an operation, and then click **New Operation**.  
  
### To remove a port operation  
  
-   Right-click the port operation to remove, and then click **Delete**.
