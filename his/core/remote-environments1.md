---
title: "Remote Environments1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3773c29-f1cc-47fb-b8b4-f5437658845a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Remote Environments
The Remote Environments folder contains definitions for the non-Windows host computers that will receive requests from the Windows-initiated processing (WIP) components. These host definitions are referred to as remote environments or REs.  
  
 The RE is used by the WIP Runtime for the following primary purposes:  
  
- Define the code page used by the host.  
  
- Define the data conversion object that will be used by the WIP Runtime.  
  
  Properties on each RE define the characteristics of the host that will be receiving requests.  
  
## REs Supported by WIP  
 WIP supports multiple types of REs (for backward compatibility reasons, there are not just two, as in host-initiated processing).  
  
 The following is a minimum set of REs that is supported:  
  
- CICS and IMS using TCP/IP  
  
- CICS LINK using LU6.2  
  
- CICS using LU6.2  
  
- IMS Connect  
  
- IMS using LU6.2  
  
  Each of the previous RE types has a (possibly) unique collection of properties, some of which are in conjunction with the Host Security functionality.  
  
### TCP/IP RE Properties  
 The basic TCP/IP RE properties contain the following:  
  
-   IP Address or Host Name  
  
-   Port List  
  
-   Receive timeout value  
  
-   Locale and Code Page  
  
-   Windows Security Context to be used (User or Package)  
  
## SNA RE Properties  
 The basic SNA RE properties contain the following:  
  
-   Local and Remote LU Aliases, Mode Name  
  
-   Receive timeout value  
  
-   Support for Sync Level 2  
  
-   Locale and Code Page  
  
-   Windows Security Context to be used (User or Package)  
  
## See Also  
 [Windows-Initiated Processing Console](../core/windows-initiated-processing-console1.md)   
 [How to View All Remote Environments](../core/how-to-view-all-remote-environments2.md)   
 [Creating a Remote Environment](../core/creating-a-remote-environment1.md)