---
description: "Learn how to configure Send and Receive shapes that will be used in a BizTalk orchestration."
title: "Task 3: Configure the Send and Receive Shapes1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e258d22-755b-48a4-9f9e-e9398f6b68b1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Task 3: How to Configure the Send and Receive Shapes

Use the following procedure to configure the Send and Receive shapes.  
  
### To configure the Send and Receive shapes  
  
1. Drag Send and Receive shapes from the tool box into the center of the orchestration in the following order.  
  
2. Set the following parameters:  
  
    |Shape|Name|Setting|  
    |-----------|----------|-------------|  
    |Receive1|Activate|True|  
    ||Message|BeginDocMsg|  
    ||Name|ReceiveBeginDoc|  
    ||Operation|BeginDoc.Operation_1.Request|  
    |Send1|Message|BeginDocSessionMsg|  
    ||Name|SendBeginDoc|  
    ||Operation|JDEPort.Operation_1.Request|  
    |Receive2|Activate|False|  
    ||Message|BeginDocResponseMsg|  
    ||Name|ReceiveBeginDocResponse|  
    ||Operation|JDEPort.Operation_1.Response|  
    |Send2|Message|EditLineSessionMsg|  
    ||Name|SendEditLine|  
    ||Operation|JDEPort.Operation_2.Request|  
    |Receive3|Activate|False|  
    ||Message|EditLineResponseMsg|  
    ||Name|ReceiveEditLine|  
    ||Operation|JDEPort.Operation_2.Response|  
    |Send3|Message|EndDocSessionMsg|  
    ||Name|SendEndDoc|  
    ||Operation|JDEPort.Operation_3.Request|  
    |Receive4|Activate|False|  
    ||Message|EndDocResponseMsg|  
    ||Name|ReceiveEndDocResponse|  
    ||Operation|JDEPort.Operation_3.Response|  
    |Send4|Message|EndDocResponseMsg|  
    ||Name|SendEndDocResponse|  
    ||Operation|EndDocOut.Operation_1.Request|  
  
## See Also
  
 [Task 1: Create the Ports](../core/task-1-create-the-ports2.md)   
 [Task 2: Create the Messages](../core/task-2-create-the-messages1.md)   
 [Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape2.md)   
 [Task 5: Configure the Transform Shape](../core/task-5-configure-the-transform-shape1.md)
