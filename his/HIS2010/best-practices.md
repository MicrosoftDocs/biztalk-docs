---
title: "Best Practices | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbe100c5-338f-447d-a9d0-06ed51fa1038
caps.latest.revision: 4
---
# Best Practices
Several rules of thumb can be applied when selecting your Host Integration Server hardware:  
  
-   Try to avoid memory paging.  
  
     It is useful to increase the amount of physical memory in a Host Integration Server computer to avoid paging. This guideline is true for any Windows Server that performs communications-related functions.  
  
-   Increase memory when using Host Print service.  
  
     When using Print service, you may need more memory on the Host Integration Server computer if large files or many print jobs are submitted. You also need adequate disk space to temporarily store the spooled print jobs.  
  
-   Use TCP/IP instead of Microsoft Networking.  
  
     The Windows Sockets (Winsock) and TCP/IP combination uses less memory on the Host Integration Server computer than Microsoft Networking or other named socket solutions. TCP/IP also provides better performance than Microsoft Networking because of its lower network overhead.  
  
## See Also  
 [Variables Affecting Hardware](../HIS2010/variables-affecting-hardware.md)   
 [Estimating Hardware Demands](../HIS2010/estimating-hardware-demands.md)   
 [Planning Your Hardware](../HIS2010/planning-your-hardware1.md)