---
description: "Learn more about: How to Run the Port Configuration Wizard"
title: "How to Run the Port Configuration Wizard"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Run the Port Configuration Wizard
You use the Port Configuration Wizard to create and configure a port in Orchestration Designer. A port must have a port type associated with it, and you use the wizard to select an existing port type or to create a new port type. For more information about ports and port types, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).  
  
### To Start the wizard  
  
1.  Right-clicking a port (on the design surface or in the Orchestration View window) and clicking **Configure Port**.  
  
2.  Running Smart Tag items whose associated actions cause a port to be created.  
  
3.  Selecting the **New Configured Port Parameter** command from the shortcut menu of the Orchestration Parameters folder in the Orchestration View window.  
  
### To Run the Wizard  
  
1.  Open the Port Configuration Wizard.  
  
2.  Specify port information. To help you, the wizard displays several pages. After completing each page, move to the following one by clicking **Next**, or move to the preceding one by clicking **Back**.  
  
    -   **Port Properties**. Type in a name for the port.  
  
    -   **Select a Port Type.** On this page, you first select whether you want a **New Port Type** or an **Existing Port Type**. If you select **Existing Port Type**, you then use a tree control to choose which existing port type to assign.  
  
         If you select **New Port Type**, you then need to type the name of the port type in the **Name** text box, or accept the suggested default name. You also select the port type's communication pattern (one-way or request-response) and any access restrictions to impose on the new port type.  
  
    -   **Port Binding**. On this page you specify the direction of communication, also known as the *polarity*, and the binding type of the port.  
  
         The polarity choice you make depends in part on the communication pattern of the port type that you selected on the preceding page of the wizard, **Select a Port Type**. Your choices are summarized in the following table:  
  
        |Port direction|Communication pattern|Direction of communication to choose on Port Binding page|  
        |--------------------|---------------------------|---------------------------------------------------------------|  
        |Send|One-way|I will always be sending messages on this port.|  
        |Receive|One-way|I will always be receiving messages on this port.|  
        |Send-Receive|Solicit-response|I will be sending a request and receiving a response.|  
        |Receive-Send|Request-response|I will be receiving a request and sending a response.|  
  
         You have a choice of four different binding types: Specify later, Specify now, Dynamic, and Direct. Each choice displays a different set of configuration options, as summarized here:  
  
         **Specify later.** After selecting this option, you make no further configuration choices in the wizard because binding information is not determined at design time. Typically it is added by an Administrator at deployment time.  
  
         **Specify now.** You can specify at design time a URI that defines the entity to which the port is to be bound. You also need to select from a list of transport types that includes BizTalk Message Queuing, FILE, SMTP, HTTP, and SOAP. This is a hard-coded list for the purpose of early binding in Orchestration Designer; therefore, other transports are not available in this list. Finally, you select a receive pipeline and a send pipeline from a list of available pipelines. The list for each includes all pipelines in the current project plus the option of selecting a pipeline from a referenced assembly, which displays the **Select Artifact Type** dialog box.  
  
         **Dynamic.** This option has similar choices to **Specify now**, but it is available only for a send port. You can specify a send pipeline to use. You can specify the port separately in an **Expression** shape so that it is assigned at run time.  
  
         **Direct.** For direct binding, you can either select a port to connect to, to do routing based on filter expressions on incoming messages in the MessageBox database, or to make it a self-correlating port. You can select a port from a drop-down list box.  
  
         For more information, see [Port Bindings](../core/port-bindings.md).  
  
3.  Complete the wizard. The final page of the Port Configuration Wizard, entitled **Completing the Port Wizard**, displays the choices you made on the preceding pages so that you can verify them before committing the changes. If the changes are correct, click **Finish**. Otherwise, click **Back** to re-enter any information you want to change. Then move through the wizard again and click **Finish** when the information displayed on the final page matches the changes you want to make.  
  
    > [!NOTE]
    >  If you are creating a new port and you click **Cancel** in the wizard at any time before finishing port configuration, the port is not created. If you were using the wizard to modify an existing port, canceling the wizard undoes any changes you have made. Otherwise, if you click **Cancel** in the wizard, the adapter is still created, but its properties are not set. You can set port properties manually in the Properties window for the port, or you can run the wizard again.  
  
## See Also  
 [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md)
