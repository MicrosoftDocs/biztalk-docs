---
title: "How to Configure an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, applications"
  - "applications, configuring"
ms.assetid: e1cd1efb-e1ea-4344-8e23-668628d6c5a9
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an Application
This topic describes how to use the BizTalk Server Administration console to configure the artifacts in an application, as follows:  

- Bind logical ports and role links to physical ports and parties.  

- Map orchestrations to the host under which they should execute.  

- Configure send and receive ports, send port groups, and receive port locations.  

  If the application does not contain at least one orchestration, send port, send port group, receive port, or receive location, the information in this topic does not apply.  

  After completing this configuration, you will be able to start the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  

> [!NOTE]
>  You can also configure artifacts individually from within the application. For more information on configuring individual artifacts, see the links at the end of this topic.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  

### To configure an application  

1. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand  **BizTalk Server Administration**, right-click the application, and then click **Configure**.  

3. In the **Orchestrations** list in the left pane, click an orchestration, configure properties as described in the following table, and then click **OK**. If there are no orchestrations in this application, the **Orchestrations** list does not display.  


   |                  Use this                  |                                                                                                               To do this                                                                                                                |
   |--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                  **Host**                  |                                                                               From the drop-down list, select a host on which to enlist the application.                                                                                |
   |    **Bindings - Inbound Logical Ports**    |                                                              Displays the name of a logical inbound port. Logical ports are found on the port surfaces in orchestrations.                                                               |
   |        **Bindings - Receive Ports**        |     From the drop-down list, select the physical receive port that you want to bind to the corresponding inbound logical port. This list includes ports in the current application as well as ports in any referenced applications.     |
   |   **Bindings - Outbound Logical Ports**    |                                                              Displays the name of a logical outbound port. Logical ports are found on the port surfaces in orchestrations.                                                              |
   | **Bindings - Send Ports/Send Port Groups** | From the drop-down list, select the send port or send port group that you want to bind to the corresponding outbound logical port. This list includes ports in the current application as well as ports in any referenced applications. |


4. In the **Messaging** list in the left pane, click **Send Ports and Send Port Groups**, configure properties as described in the following table, and then click **OK**. This list displays all of the send ports and send port groups in the current application.  


   |    Use this    |                                                                                                                                                                                                                                To do this                                                                                                                                                                                                                                 |
   |----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **New**     |                                      Click to create a new send port or send port group. Options for send ports are identical to the options available when you right-click the **Send Ports** node in the console tree and point to **New**. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Also see [How to Create a Send Port Group](../core/how-to-create-a-send-port-group.md).                                       |
   | **Properties** | Click to display properties for the selected send port or send port group. If you select a send port, the **Send Port Properties** page displays, where you can configure the port. If you select a send port group, the **Send Port Groups Properties** page displays, where you can configure the send port group. For more information on configuring properties, see [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md). |
   |    **Name**    |                                                                                                                                                                                                               Displays the name of the physical send ports.                                                                                                                                                                                                               |
   |   **Filter**   |                                                                                                                                                                            Displays the filter expression applied to the send port. Filters are set up in the **Send Port Properties** window.                                                                                                                                                                            |
   |    **URI**     |                                                                                                                                                                                                                  Displays the URI for the selected port.                                                                                                                                                                                                                  |


5. In the **Messaging** list in the left pane, click **Receive Ports and Locations**, configure properties as described in the following table, and then click **OK**. This list displays all of the receive ports and receive locations in the current application.  


   |    Use this    |                                                                                                                                                                                                                                                                                               To do this                                                                                                                                                                                                                                                                                               |
   |----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **New**     |                                                                                                                                                 Click to create a new receive port. Options for new receive ports are identical to the options available when you right-click the **Receive Ports** node in the console tree and point to **New**. For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).                                                                                                                                                  |
   | **Properties** | Click to display properties for the selected item. If you have selected a receive port, the **Receive Port Properties** page displays, where you can configure the port. If you have selected a receive location, the **Receive Locations Properties** page displays, where you can configure the receive location. To select a receive port, click the boldface text to the right of **Receive port**. For more information on configuring properties, see [Managing Receive Ports](../core/managing-receive-ports.md). Also see [Managing Receive Locations](../core/managing-receive-locations.md). |
   |    **Name**    |                                                                                                                                                                                                                                                               Displays the name of the receive location associated with a receive port.                                                                                                                                                                                                                                                                |
   |    **URI**     |                                                                                                                                                                                                                                                                          Displays the URI for the selected receive location.                                                                                                                                                                                                                                                                           |


6. In the left pane, click **Role Links**, configure properties described in the following table, and then click **OK**. If there are no role links in the application, the **Role Links** link does not display.  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Enlist**|Click to display the **Enlist Parties** dialog box, where you can select a party to participate in the interchange defined by the role.|  
   |**Unenlist**|Click to remove the selected party from participating in the interchange.|  
   |**Bind**|Click to establish a connection between the role link and the physical ports via a party.|  
   |**Party**|Displays the name of the party or parties that you have enlisted to this role.|  

## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [Managing Role Links](../core/managing-role-links.md)   
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)   
 [Managing Receive Ports](../core/managing-receive-ports.md)   
 [Managing Receive Locations](../core/managing-receive-locations.md)