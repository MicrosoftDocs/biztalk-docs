---
title: "Security Features in the Data Providers for Host Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b12a23d2-47e1-4e20-92be-0142617c69ad
caps.latest.revision: 3
---
# Security Features in the Data Providers for Host Files
This topic describes security features in the data providers for host files.  
  
 **The Data Provider stores the user name in plain text in the Universal Data Link (UDL) or connection string file**  
  
 By default, when you use the Data Source Wizard or Data Links, the Microsoft OLE DB Provider for DB2 (Data Provider) stores the user name in plain text in the Universal Data Link (UDL) or connection file. We recommend that you configure the Data Provider to use Enterprise Single Sign-On, which integrates Windows Active Directory accounts with IBM host system and host file system credentials. As an administrator, you can map host file system credentials to AD accounts, which are stored in an encrypted SQL Server database. The Data Provider retrieves these mappings at runtime to securely authenticate users to remote IBM host file system servers.  
  
 **The Data Provider connects by using unencrypted, plain text, user name and password**  
  
 By default, the Data Provider connects to remote host file system server computers over a network relying on unencrypted, plain text, user name and password. We recommend that you configure the Data Provider to use authentication encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 when you connect to remote host file system server computers that are running i5/OS.  
  
 **The Data Provider sends and receives unencrypted data**  
  
 By default, the Data Provider sends and receives unencrypted data. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 when you connect to remote host file system server computers that are running i5/OS.  
  
## See Also  
 [Security and Protection](../HIS2010/security-and-protection3.md)