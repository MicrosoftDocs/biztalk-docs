---
title: "Secure your Oracle Database applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapter, security"
  - "authorization"
  - "data protection"
  - "adapter, data protection"
  - "authentication"
  - "security"
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Secure your Oracle Database applications
## Data protection and security overview
A database often contains sensitive business information such as customer account details. Applications that use the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission. Data protection and security are usually thought of in the following terms:  
  
- *Authorization* controls access to a resource based on the identity of the requester.  
  
- *Authentication* provides mechanisms for verifying the identity of a requester.  
  
- *Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.  
  
- *Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.  
  
  Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. The adapter uses these credentials to open connections to the Oracle database. These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.  
  
  The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## In this section  
  
-   [Security between the Oracle Database and the adapter](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [Security with the Oracle Database adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [Secure programming with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [Best practices](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)