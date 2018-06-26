---
title: "Step 2: Configure Load Test Controller and Agent Computers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Configure Load Test Controller and Agent Computers

## Overview
Visual Studio can generate load simulating up to 250 virtual users on a local load test run. To simulate more than 250 virtual users and/or to initiate testing from a remote computer requires Visual Studio Load Test Virtual User.  
  
 All load testing performed for this guide was initiated from two computers:  
  
- One computer running as both a Load Test Controller and a Load Test Agent.  
  
- Another computer running as a Load Test Agent only.  
  
  Test results were stored in a remote load test results repository in a SQL Server database.  
  
  For more information about using test controllers and test agents to distribute load tests across multiple test machines, see [Distributing Load Tests Across Multiple Test Machines Using Test Controllers and Test Agents](https://msdn.microsoft.com/library/dd728093.aspx).  
  
## Install and Configure the Load Test Controller and Load Test Agents  
 To install and configure the load test controller and load test agents, see [Install and configure test agents](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents).
