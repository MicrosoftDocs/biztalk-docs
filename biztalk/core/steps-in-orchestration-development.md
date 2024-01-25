---
description: "Learn more about: Steps in Orchestration Development"
title: "Steps in Orchestration Development"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Steps in Orchestration Development
To develop an orchestration, you typically perform the following basic actions:  
  
-   Add shapes to represent your business processes.  
  
     Orchestration Designer provides you with a toolbox of shapes that can be used to represent different actions or other abstractions. For more information, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
-   Define schemas to describe the format of your messages.  
  
     You can define schemas with BizTalk Editor. For more information, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).  
  
-   Define ports through which messages are sent and received.  
  
     You can define ports to specify how and where messages are sent and received. For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).  
  
-   Bind **Send** and **Receive** shapes to ports.  
  
     You can connect your **Send** and **Receive** shapes to ports and specify the port operations that they use. For more information, see [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md). Also see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).  
  
-   Assign or transform data between messages.  
  
     You can use the **Construct Message** shape to assign message values or do message transformations. For more information, see [Constructing Messages](../core/constructing-messages.md).  
  
-   Identify any custom components that you might want to write or add as reference to work within your orchestration.  
  
> [!NOTE]
>  If the **Copy Local** property of the referenced assembly is set to **True**, Orchestration will not be able to pick up any changes made to the external assembly after the initial add reference takes place in BizTalk project.  
  
-   Define and assign orchestration variables to manage data in your running orchestration.  
  
     You can use the Variables folder in the Orchestration View window to declare your orchestration variables, and BizTalk Expression Editor to edit expressions that assign and use the variables in various shapes. For more information, see [XLANG-s Data Types](../core/xlang-s-data-types.md).  
  
-   Build your orchestration to test it for completeness.  
  
     You build your orchestration when you compile the project or solution that contains it. For more information, see [How to Build Orchestrations](../core/how-to-build-orchestrations.md).  
  
## See Also  
 [Building and Running Orchestrations](../core/building-and-running-orchestrations.md)   
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md)
