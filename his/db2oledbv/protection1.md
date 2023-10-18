---
description: "Learn about the supported standards for IBM DB2 protection, including encryption standards and configuring for protection."
title: "Protection1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protection

This topic describes supported standards for DB2 protection.  
  
## Encryption standards for DB2
  
The following table describes supported encryption standards for DB2.  
  
|Encryption|Authentication|Data|  
|----------------|--------------------|----------|  
|Kerberos|Yes|No|  
|Secure Sockets Layer (SSL) V3|Yes|Yes|  
|Transport Layer Security (TLS) V1|Yes|Yes|  
|Advanced Encryption Standard (AES)|Yes|No|  
  
## Configuring for Protection  
  
### Data Provider grants execute on DB2 package to the DB2 public group  
 When you create DB2 packages, the Data Access Tool and the Data Provider set the execute permissions on DB2 packages to PUBLIC, which includes all DB2 users. To increase security on your DB2 server, we recommend that you revoke the execute permissions to PUBLIC on these packages and grant execute permissions only to selected DB2 users or groups.  
  
### Data Tools store the authentication credentials in plain text in the Universal Data Link (UDL) file  
 Data Source Wizard and Data Links store the authentication credentials (user name and password) in plain text in the Universal Data Link (UDL) or connection string (TXT) file. We recommend that you configure the Data Provider to use Enterprise Single Sign-On (ESSO), which securely stores mappings from Windows Active Directory accounts to IBM DB2 credentials. The Data Provider retrieves these mappings at runtime to securely authenticate Windows users to remote IBM DB2 database servers. You should run the Data Provider in-process with the Data Consumer and Data Tools.  

### Data Provider connects using unencrypted, plain text, user name and password  
 Data Provider connects to remote DB2 server computers over a TCP/IP or SNA network using basic authentication, where the user name and password are not encrypted and are submitted in plain text. We recommend that you configure the Data Provider to use authentication encryption by using Kerberos, Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0, or authentication encryption using AES.  
  
### Data Provider sends and receives unencrypted data  
 Data Provider sends and receives unencrypted data. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0.  
  
### Data Consumers and Data Tools read and write connection files to and from unsecure folders  
 Data Consumers and Data Tools can read and write connection files to and from unsecure folders. You should store Universal Data Link (UDL) files in the Host Integration Server\Data Sources or a program directory, and then secure the folder with local administrator rights. You should persist the connection information into the Data Consumers and Data Tools secure stores, and then run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### Data Consumers and Data Tools can request connections with invalid properties  
 Data Consumers and Data Tools can request connections with invalid connection property values. You should use the Data Consumers that create connections using the Data Provider connection objects instead of passing unverified connection string argument name value pairs. You should set a connection timeout value to cancel invalid connection attempts.  
  
### Data Consumers and Data Tools can request commands with invalid data  
 Data Consumers and Data Tools can request commands with invalid data. You should use the Data Consumers that create commands using the Data Provider command with parameter objects, to validate parameter types, instead of passing unverified command strings with in-line data values. You should set a command timeout value to cancel invalid command attempts. You should use DRDA distributed unit of work (DUW), instead of remote unit of work (RUW), to protect the Data Consumers using two-phase commit transactions.
