---
title: "Installing Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, installing"
  - "installing, certificates"
ms.assetid: 7525f771-623c-420f-99ca-c834e819829d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing Certificates
To send, repair, or submit messages, you must have the proper certificates installed. This topic describes how to add certificates. In a production environment, see your IT department for certificates.  

 **Summary**  

 This section provides instructions on how to create and store the following certificates:  

- Certificates for each of the Message Repair and New Submission roles in the Personal folder of the Certificates - Current User store on each client computer  

- Certificates for each of the Message Repair and New Submission roles in the Other People folder of the Certificates (Local Computer) store on each BizTalk orchestration server computer  

- Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) store on each client computer  

  If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer, and also have a certificate server installed on the same computer, you need to exclude the certificate server from the managed paths for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server.  

  This section contains:  

- [Adding Certificates to the Certificates Store on the Client](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  

- [Adding Certificates to the Certificates Store on the Server](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  

- [Excluding CertSrv from Managed Paths on a Single-Computer Deployment](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)
