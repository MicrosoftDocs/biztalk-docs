---
description: "Learn more about: Task 1: Create the Ports"
title: "Task 1: Create the Ports1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b944a03-c8e2-4eba-9e11-10c14f929499
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Task 1: How to Create the Ports
Create the following ports, BeginDoc and EndDocOut on the left and JDEPort with 3 operations on the right.  
  
|Name and Settings|Operation|Message Type > Schema|  
|-----------------------|---------------|----------------------------|  
|BeginDoc<br /><br /> BeginDocType / One-Way / Internal<br /><br /> I'll always be receiving messages on this port<br /><br /> Specify Later|Operation 1 Request -|BeginDocTest.B4200310Service_1.<br />F4211FSBeginDoc|  
|EndDocOut<br /><br /> EndDocType / One-Way / Internal<br /><br /> I'll always be sending messages on this port<br /><br /> Specify Later|Operation 1 Request -|BeginDocTest.B4200310Service_1.<br />F4211FSEndDocResponse|  
|JDEPort<br /><br /> JDEPortType / Request-Response / Internal<br /><br /> I'll always be sending a request and receiving a response<br /><br /> Specify Later **Note:**  For additional operations, right-click the port and select New Operation.|Operation 1 Request -<br /><br /> Operation 1 Response -<br /><br /> Operation 2 Request -<br /><br /> Operation 2 Response -<br /><br /> Operation 3 Request -<br /><br /> Operation 3 Response -|BeginDocTest.B4200310Service_1.<br />F4211FSBeginDoc<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSBeginDocResponse<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEditLine<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEditLineResponse<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEndDoc<br /><br /> BeginDocTest.B4200310Service_1.<br />F4211FSEndDocResponse|  
  
## See Also  
 [Task 2: Create the Messages](../core/task-2-create-the-messages2.md)   
 [Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md)   
 [Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md)   
 [Task 5: Configure the Transform Shape](../core/task-5-configure-the-transform-shape2.md)
