---
title: "Multithreaded APINGD | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd888080-30e0-4236-a5de-9342a80411dc
caps.latest.revision: 4
---
# Multithreaded APINGD
The version of MPINGD provided in the sample code illustrates how to achieve nonqueued behavior from an invokable TP in Microsoft Windows. This means that multiple copies of APING can talk to the same copy of MPINGD at the same time. However, you cannot run multiple copies of a Windows service. The features are achieved by always having a thread with an [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md) outstanding, so that any incoming attach for MPINGD will always be satisfied immediately.  
  
## Setup  
 Setup requirements for MPINGD are the same as for the single-threaded version, APINGD. The remote LU and mode that you use should support parallel sessions so that more than one conversation at a time is possible.  
  
## Input and Output  
 The input and output for MPINGD are the same as for the single-threaded version, APINGD.  
  
## Operation  
 The operation of MPINGD is similar to that of the single-threaded version, APINGD. The same three routines are used (**main**, **ServiceMain** and **ControlHandler**). **ServiceMain** calls the **TPStart** routine. This routine must not return until the service is ready to terminate.  
  
 The **TPStart** routine does some initialization, creates the first conversation thread, and then waits on an event created by the **ServiceMain** routine. This event is set when the service control manager issues an order to STOP or SHUTDOWN. When the event is set, it calls [WinCPICCleanup](../HIS2010/wincpiccleanup1.md), which will cancel any active conversations and return outstanding [Accept_Conversation](../HIS2010/accept-conversation-cpi-c-1.md) calls, thus making all conversation threads exit. It then marks the service as STOPPED.  
  
 The **ThreadStart** routine is the entry point for each of the conversation threads. It issues **Accept_Conversation** and [Wait_For_Conversation](../HIS2010/wait-for-conversation-cpi-c-2.md), and when this completes, it creates another thread to wait for the next attach while the existing thread services the first attach.  
  
## See Also  
 [CPI-C Samples](../HIS2010/cpi-c-samples.md)