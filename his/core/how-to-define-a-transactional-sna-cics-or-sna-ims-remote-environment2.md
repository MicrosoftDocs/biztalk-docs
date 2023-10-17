---
description: "Learn more about: How to Define a Transactional SNA CICS or SNA IMS Remote Environment"
title: "How to Define a Transactional SNA CICS or SNA IMS Remote Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b26eea7-dd97-466e-a52e-c0cf7231daed
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Define a Transactional SNA CICS or SNA IMS Remote Environment
A transactional SNA CICS or SNA IMS remote environment (RE) is one that supports Sync Level 2 to enable two-phase commit (2PC). Note that none of the TCP/IP REs support 2PC because TCP/IP does not support Sync Level 2 or any other 2PC mechanism.  
  
 Note that IMS version 6.0 and IBM Resource Recovery Service (RRS) are required on the mainframe system for IMS sync level 2 support.  
  
### To define a transactional SNA CICS or SNA IMS RE  
  
1.  Start TI Manager.  
  
2.  Create a new CICS Using LU 6.2, CICS LINK Using LU 6.2, or IMS Using LU 6.2 RE, or click an existing SNA RE in the console tree.  
  
     To create a new RE, double-click **Transaction Integrator** in the console tree, right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.  
  
3.  Right-click **CICS Using LU 6.2**, **CICS LINK Using LU 6.2**, or **IMS Using LU 6.2 RE**, and then click **Properties**.  
  
4.  Click the **LU 6.2** tab.  
  
5.  Select the **Supports Sync Level 2 Protocols** check box.  
  
## See Also  
 [Creating and Managing Remote Environments with TI Manager](../core/creating-and-managing-remote-environments-with-ti-manager1.md)   
 [Getting Started with TI](../core/getting-started-with-ti1.md)
