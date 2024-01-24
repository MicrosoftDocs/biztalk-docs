---
description: "Learn more about: Host Integration Server to Host Problems"
title: "Host Integration Server to Host Problems1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Host Integration Server to Host Problems
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Services cannot connect to a host over the Microsoft Networking (Names Pipes) protocol. High Performance Routing over Internet Protocol (HPR/IP) and TCP/IP (TN3270 and TN5250) are the protocols commonly used to connect from the server to a host. If you cannot get an emulation session at the server itself, check the status of the connection using the SNA Manager. If the status is "Active", but you cannot access an emulation session, there may be a configuration problem.
  
 If the status is "Inactive" or "Pending", the communication between the server and the host is failing.  
  
 Check the Application and System Event Logs. Most often, "Pending" or "Inactive" connections will produce an event in the Applications Log – usually an event 230 or 23. The text of these messages varies and can indicate the nature of the problem. If the problem is the result of hardware failure, the event will usually be logged in the System Log. If the connection has been functional in the past, there may be a communications problem. For example, an SDLC connection may fail due to phone line problems.
