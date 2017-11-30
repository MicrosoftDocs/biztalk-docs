---
title: "Special Security Settings for TCP-IP1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1474e13-b786-4694-92bd-359d53cb4c6e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Special Security Settings for TCP/IP
Two special security settings are available for the TCP/IP protocol for CICS and IMS:  
  
-   Link and Concurrent Server Mainframe authentication for the TCP/IP CICS MS Link and Concurrent server must have a user exit, EZACIC06, coded on the mainframe to validate the user ID and password supplied by TI. The user ID and password are part of the CICS transaction request message that is formatted by TI and used to initiate the TCP/IP server application in CICS. Refer to the IBM TCP/IP and CICS documentation for further detail.  
  
-   For TCP/IP IMS Connect or OTMA Mainframe authentication must have user exit, IMSLSECX, coded on the mainframe to validate the user ID and password supplied by TI. The user ID and password are part of the IMS transaction request message that is formatted by TI and used to initiate the TCP/IP server application in IMS. Refer to the IBM TCP/IP and IMS documentation for further detail.  
  
## See Also  
 [Application Integration (Security)](../core/application-integration-security-2.md)