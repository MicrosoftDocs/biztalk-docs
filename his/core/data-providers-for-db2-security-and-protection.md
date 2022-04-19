---
description: "Learn more about: Data Providers for DB2 Security and Protection"
title: "Data Providers for DB2 Security and Protection | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14be5afc-f7c0-44b5-a9c9-80f0eccebe6b
caps.latest.revision: 6
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Data Providers for DB2 Security and Protection
You can use the data providers for DB2 (Data Provider) to connect Windows data consumer applications to remote IBM DB2 relational database management servers. The Data Provider function as a distributed relational database architecture (DRDA) application requester client that supports the DRDA protocol and formats that are compatible with IBM DB2 server products functioning as DRDA application servers.  
  
 You can use the Data Provider by issuing structured query language statements. These statements include data definition language statements for administration and data manipulation management statements for read and write operations. The Data Provider connects the Windows client applications to the DB2 server databases across a transmission control protocol over an Internet protocol (TCP/IP) network or Systems Network Architecture (SNA) high performance routing over internet protocol (HPR/IP) that use one or more of the optional security features described later in this topic.  
  
## Security  
  
## User Account  
 The Data Provider tools, Data Access Tool and Data Links, run in the context of a user account. The user account must be a member of the HIS Administrators and HIS Runtime Users Local Groups.  
  
## Folder Access Control List  
 The user account requires the Folder Access Control List settings associated with the HIS Administrators Local Group and HIS Runtime Users Local Group.  
  
 Program Files\Microsoft Host Integration Server 2013  
Program Files\Microsoft Host Integration Server 2013\system  
Program Files\Microsoft Host Integration Server 2013\ SysWOW64  
Program Files\Microsoft Host Integration Server 2013\traces  
Documents\Host Integration Server\Data Sources  
  
## Protection  
  
### Data Provider grants execute on DB2 packages to the DB2 public group  
 When you create DB2 packages, the Data Access Tool and the Data Provider set the execute permissions on DB2 packages to PUBLIC, which includes all DB2 users. To increase security on your DB2 server, we recommend that you revoke the execute permissions to PUBLIC on these packages and grant execute permissions only to selected DB2 users or groups.  
  
### Data Tools store the authentication credentials in plain text in the Universal Data Link (UDL) or connection string (TXT) file  
 Data Source Wizard and Data Links store the authentication credentials (user name and password) in plain text in the Universal Data Link (UDL) or connection string (TXT) file. We recommend that you configure the data providers to use Enterprise Single Sign-On (ESSO), which securely stores mappings from Windows Active Directory accounts to IBM DB2 credentials. The data providers retrieve these mappings at runtime to securely authenticate Windows users to remote IBM DB2 database servers. You should run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### DRDA supports weak built-in encryption based on DES  
 DRDA supports built-in authentication and data encryption using weak 56-bit Data Encryption Standard (DES) technologies. We recommend that you configure the Data Provider to use strong data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0. For encrypting authentication only, you can utilize the Advanced Encryption Standard (AES) to support strong 256-bit encryption.  
  
### Data Provider connects by using unencrypted, plain text, user name and password  
 Data Provider connects to remote DB2 server computers over a TCP/IP or SNA network using basic authentication, where the user name and password are not encrypted and are submitted in plain text. We recommend that you configure the Data Provider to use authentication encryption by using Kerberos, Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0, or authentication encryption using AES.  
  
### Data Provider sends and receive unencrypted data  
 Data Provider sends and receives unencrypted data. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0.  
  
### Encryption standards for DB2  
 The following table describes supported encryption standards for DB2.  
  
|Encryption|Authentication|Data|  
|-|-|-|  
|Kerberos|Yes|No|  
|SSL V3|Yes|Yes|  
|TLS V1|Yes|Yes|  
|AES|Yes|No|  
  
### Data Consumers and Data Tools read and write connection files to and from unsecure folders  
 Data Consumers and Data Tools can read and write connection files to and from unsecure folders. You should store Universal Data Link (UDL) or connection string (TXT) files in the Host Integration Server\Data Sources or a program directory, and then secure the folder with local administrator rights. You should persist the connection information into the Data Consumers and Data Tools secure stores, and then run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### Data Consumers and Data Tools can request connections with invalid properties  
 Data Consumers and Data Tools can request connections with invalid connection property values. You should use the Data Consumers that create connections using the Data Provider connection objects instead of passing unverified connection string argument name value pairs. You should set a connection timeout value to cancel invalid connection attempts.  
  
### Data Consumers and Data Tools can request commands with invalid data  
 Data Consumers and Data Tools can request commands with invalid data. You should use the Data Consumers that create commands using the Data Provider command with parameter objects, to validate parameter types, instead of passing unverified command strings with in-line data values. You should set a command timeout value to cancel invalid command attempts. You should use DRDA distributed unit of work (DUW), instead of remote unit of work (RUW), to protect the Data Consumers using two-phase commit transactions.  
  
## See Also  
 [Security and Protection](../core/security-and-protection1.md)
