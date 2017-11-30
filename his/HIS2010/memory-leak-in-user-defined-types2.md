---
title: "Memory Leak in User-Defined Types2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d741343a-c077-4346-a1e3-7bf2a3a1ac1e
caps.latest.revision: 4
---
# Memory Leak in User-Defined Types
If Microsoft COM Transaction Integrator (COMTI) is configured to use a "Customer Information Control System (CICS) or Information Management System (IMS) by using TCP/IP" Remote Environment (RE), and a client application repeatedly calls the COM+ component, which in turn instantiates COMTI objects by using user-defined types, eventually the application might fail and return the following error message:  
  
 **Method %1 of Object %2 failed**  
  
> [!NOTE]
>  Other REs may exhibit the same problem.  
  
 If you use Microsoft Windows System Monitor to log data for the Private Bytes and Working Set of the Process object, a memory leak occurs.  
  
 The problem is caused by having Occurs Depending On (ODO) arrays in a user-defined type. Specifically, a call is made to obtain a VarDesc structure from a type library, and a free method call is never issued to release the memory back to the operating system.