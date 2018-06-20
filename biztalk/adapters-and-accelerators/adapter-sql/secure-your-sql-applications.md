---
title: "Secure your SQL applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Secure your SQL applications
## Overview
SQL Server databases often contain sensitive business information such as customer account details. Applications that use the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission. Data protection and security are usually thought of in the following terms:  
  
- *Authorization* controls access to a resource based on the identity of the requestor.  
  
- *Authentication* provides mechanisms for verifying the identity of a requestor.  
  
- *Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.  
  
- *Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.  
  
  Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. The adapter uses these credentials to open connections to the SQL system. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not allow credentials to be supplied in the connection URI. This prevents the credentials from getting exposed inadvertently. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides two alternative methods to supply these credentials in a more secure manner:  
  
  Integrated Security. In this case, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] credentials. You must configure the SQL server to accept these credentials for this method to work.  
  
  Enterprise Single Sign-on (SSO). For more information about using SSO, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) .  
  
  The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## In This Section  
  
-   [Security between the SQL Server and the adapter](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [Secure programming with the SQL adapter](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [Best practices](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)