---
title: "How to Work with Port Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, port types"
  - "port types, deleting"
  - "port types, Web"
  - "port types, request-response"
  - "orchestrations, ports"
  - "port types, modifier"
  - "port types"
  - "ports, port types"
  - "port types, one-way"
ms.assetid: 78ac731e-c330-4888-a9ee-10523fef8ed0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Work with Port Types
A port type consists of a communication pattern, a set of operations (requests or responses), and the message types that those operations can work on. The pattern can be either one-way or request-response (two-way), and all operations defined on that port type must use the same pattern. Note that port types are direction-agnostic: direction is specified on individual ports.  
  
 The scope of a port type is defined by the **Type Modifier** property. A port type can be public, private, or internal. If it is public, it is visible to anyone interacting with the orchestration. If it is private, it is visible to other orchestrations within the same project and namespace. If it is internal, the port type is visible only within the project. Since a port type definition includes message types, the scope of the message type must encompass that of any port type that uses it.  
  
> [!NOTE]
>  A port type can be applied to any number of ports. You can think of a port as an instance of a port type.  
  
> [!NOTE]
>  A port type does not inherently have a communication direction; you set direction on individual ports.  
  
### To add a request-response port type  
  
1.  In the Orchestration View window, right-click **Port Types** and then click **New Request-response Port Type**.  
  
     The **Port Types** node expands, if collapsed, and a new request-response port type is added with one default operation.  
  
2.  Specify a name for the port type.  
  
3.  Define one or more port operations.  
  
     You can name your port operations, but when you are selecting them from another project, you will see them only as "Request" and "Response." If you select a port operation from another project, verify that it has the correct message type.  
  
### To add a one-way port type  
  
1.  In the Orchestration View window, right-click **Port Types** and then click **New One-way Port Type**.  
  
     The **Port Types** node expands, if collapsed, and a new one-way port type is added with one default operation.  
  
2.  Specify a name for the port type.  
  
3.  Define one or more port operations.  
  
### To add a Web port type  
  
-   Add a project reference to an assembly containing a proxy class for a Web service. For more information, see [Creating Web Ports](../core/creating-web-ports.md).  
  
### To remove a port type  
  
-   In the Orchestration View window, right-click the port type to delete, and then click **Delete**.  
  
    > [!NOTE]
    >  If the port type is in use, deleting it will impact the configuration of any ports that are configured to use it.  
  
    > [!NOTE]
    >  Items that appear as read-only are defined in another orchestration.  
  
### To set the type modifier for a port type  
  
-   In the Properties window, set the following property:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Type Modifier|Determines the scope of the port type:<br /><br /> Private—Access to this port type is limited to the containing module.<br /><br /> Public—Access to this port type is not limited.<br /><br /> Internal—Access to this port type is limited to modules within the same project.|  
  
## See Also  
 [Communication Pattern](../core/communication-pattern.md)   
 [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md)   
 [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md)