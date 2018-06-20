---
title: "Step 1 (L) Creating and Configuring Link Services1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df8209a8-9864-4a18-b393-9051c05ce65c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Step 1 (L) Creating and Configuring Link Services
This section details creating and configuring link services. The maximum number of 802.2 link services that one Host Integration Server computer can support is:  
  
- 64 per network adapter (limited by SAP)  
  
- 255 per SNA server (limited by index from 0x01 to 0xFF)  
  
  However, SNA Manager allows only 64 link services per Host Integration Server computer, no matter how many adapters are installed on the server. To configure the number higher than this, use the utility Linkcfg.exe.  
  
  For information on the new IP-DLC Link Service, see [IP-DLC Link Service](./ip-dlc-link-service2.md).  
  
## In This Section  
 [Creating Link Services](../core/creating-link-services1.md)  
  
 [Configuring Link Services](../core/configuring-link-services1.md)  
  
## See Also  
 [Making and Testing a Connection](../core/making-and-testing-a-connection2.md)