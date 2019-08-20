---
title: "Data Encryption2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50b72d46-bc94-4e09-b7ca-7cc7ffea9f53
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Data Encryption
Data Encryption helps secure traffic between the client computer and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] on a per-user basis. There is a client component and a server component. The data encryption is implemented transparently to any application that is written to the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] APIs (application program interfaces). Any software, such as a third-party emulator, that is written to use the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] client APIs will automatically benefit from the encryption.  
  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] lets you encrypt data for client-to-server and server-to-server communications.  
  
 Client-to-server encryption prevents information from being sent in clear text between Host Integration Server client workstations and Host Integration Server computers. Data encryption enhances network security on the client-to-server communications path for all applications using Host Integration Server client connections, including 3270/5250 emulators and APPC logon IDs and passwords. Data encryption is enabled by default.  
  
 Server-to-server encryption can be used to help provide more secure communications across your network, the Internet, or any other wide area network. If a user enables data encryption, information transferred through Distributed Link Service (DLS) is automatically more secure.  
  
 Host Integration Server lets you encrypt data for client-to-server and server-to-server communications.  
  
 Client-to-server encryption prevents information from being sent in clear text between Host Integration Server client workstations and Host Integration Server computers. Data encryption enhances network security on the client-to-server communications path for all applications using Host Integration Server client connections, including 3270/5250 emulators and APPC logon IDs and passwords. You can enable data encryption on a user-by-user basis using the Host Integration Server SNA Manager.  
  
 Server-to-server encryption can be used to provide more secure communications across your network, the Internet, or any other wide area network. If a user enables data encryption, information transferred through the Distributed Link Service (DLS) is automatically secure.  
  
 Data encryption is enabled for Distributed Link Service by adding the domain user account under which Host Integration Server services such as SnaBase or SnaServer are running to the SNA subdomain. The actual encryption is implemented in the transport providers layer of the Host Integration Server architecture. You can then enable data encryption settings for the user account, as described above.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)