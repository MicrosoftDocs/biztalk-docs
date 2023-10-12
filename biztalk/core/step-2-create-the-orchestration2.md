---
description: "Learn how to setup and create a BizTalk orchestration for the J.D. Edwards EnterpriseOne system."
title: "Step 2: Create the Orchestration2"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 2: Create the Orchestration

The orchestration setup is as follows using a project called BeginDocTest:  
  
 • Ports  
  
 • Messages  
  
 • Send and Receive  
  
 • Construct Message  
  
 • Transforms  
  
 The orchestration does not do any exception handling. J.D. Edwards EnterpriseOne performs the BeginDoc and subsequent operations within an implicit transaction that it will rollback if the connection times out. The BizTalk orchestration thus does not need to do anything to rollback changes J.D. Edwards EnterpriseOne makes. However, a time out will cause an exception in the BizTalk orchestration. BizTalk will record the exception in the event log. If you want to add exception handling to the orchestration, see "How to Add a Catch Exception Block" and "How to Add a Compensation Block" in the Microsoft BizTalk 2006 main help.  
  
## In This Section  
  
- [Task 1: Create the Ports](../core/task-1-create-the-ports1.md)  
  
- [Task 2: Create the Messages](../core/task-2-create-the-messages2.md)  
  
- [Task 3: Configure the Send and Receive Shapes](../core/task-3-configure-the-send-and-receive-shapes2.md)  
  
- [Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md)  
  
- [Task 5: Configure the Transform Shape](../core/task-5-configure-the-transform-shape2.md)
