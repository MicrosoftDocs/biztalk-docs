---
title: "Security Features in the Data Providers for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fc8bbe0-01d0-42be-9533-8b29562c26aa
caps.latest.revision: 6
---
# Security Features in the Data Providers for DB2
You can use the data providers for DB2 to connect data consumer applications to remote IBM DB2 relational database management servers. The data providers function as a DB2 application requester client that supports the standard distributed relational database architecture (DRDA) protocols and formats that are compatible with IBM DB2 server products, which function as DB2 application servers.  
  
 You can use the data providers by issuing structured query language statements. These statements include data definition language statements for administration and data manipulation management statements for read and write operations. The data providers connect the DB2 client applications to the DB2 server databases across a transmission control protocol over an Internet protocol (TCP/IP) network or Systems Network Architecture (SNA) high performance routing over internet protocol (HPR/IP) that use one or more of the optional security features described later in this topic.  
  
 **The data providers grant execute on DB2 package to the DB2 public group**  
  
 When you create DB2 packages, the Data Access Tool and the data providers set the execute permissions on DB2 packages to PUBLIC, which includes all DB2 users. To increase security on your DB2 server, we recommend that you revoke the execute permissions to PUBLIC on these packages and grant execute permissions only to selected DB2 users or groups. Permissions granted to PUBLIC are granted to all DB2 users, which could leave your DB2 server vulnerable to attack.  
  
 **The data providers store the user name in plain text in the Universal Data Link (UDL) or connection string file**  
  
 By default, when you use the Data Source Wizard or Data Links, the data providers store the user name in plain text in the Universal Data Link (UDL) or connection file. We recommend that you configure the data providers to use Enterprise Single Sign-On, which integrates Windows Active Directory accounts together with IBM host system and DB2 credentials. Administrators map host and DB2 credentials to AD accounts, which are stored in an encrypted SQL Server database. The providers retrieve these mappings at runtime to securely authenticate users to remote IBM DB2 database servers.  
  
 **The data providers support weak encryption based on DES**  
  
 Optionally, the data providers support authentication and data encryption using weak 56-bit Data Encryption Standard (DES) technologies. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0. For encrypting authentication only, you can utilize the Advanced Encryption Standard (AES) to support 256-bit encryption.  
  
 **The data providers connect by using unencrypted, plain text, user name and password**  
  
 By default, the data providers connect to remote DB2 server computers over a TCP/IP or SNA network using basic authentication, where the user name and password are not encrypted and are submitted in plain text. We recommend that you configure the data providers to use authentication encryption by using Kerberos, Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0, or authentication encryption using AES.  
  
 **The data providers send and receive unencrypted data**  
  
 By default, the data providers send and receive unencrypted data. We recommend that you configure the data providers to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0.  
  
 **Encryption standards for DB2**  
  
 The following table describes supported encryption standards for DB2.  
  
|||||||  
|-|-|-|-|-|-|  
|**Encryption**|**Authentication**|**Data**|**DB2 for z/OS**|**DB2 for i5/OS**|**DB2 for LUW**|  
|Kerberos|Yes|No|V8|V5R3|V8|  
|SSL V3|Yes|Yes|V9|V5R4|V9.1|  
|TLS V1|Yes|Yes|V9|V5R4|V9.1|  
|AES|Yes|No|V8 (APAR PK56287)|V5R4|V9.5 (Fix Pack 3)|  
  
## See Also  
 [Security and Protection](../HIS2010/security-and-protection3.md)