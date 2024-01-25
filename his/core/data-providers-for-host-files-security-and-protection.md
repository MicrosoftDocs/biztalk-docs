---
description: "Learn more about: Data Providers for Host Files Security and Protection"
title: "Data Providers for Host Files Security and Protection"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Providers for Host Files Security and Protection
You can use the ADO.NET Provider for Host Files (Data Provider) to connect Windows data consumer applications to remote IBM host file system servers. The data provider functions as a distributed data management (DDM) client that supports the record-level input/output (RLIO) protocol that are compatible with IBM host file server products functioning as DDM servers.  
  
 You can use the data provider by issuing structured query language statements for read and write operations. The data provider connects the Windows client applications to the host file servers across a transmission control protocol over an Internet protocol (TCP/IP) network or Systems Network Architecture (SNA) high performance routing over internet protocol (HPR/IP) that use one or more of the optional security features described later in this topic.  
  
## Security  
  
## User Account  
 The Data Provider tools, Data Access Tool and Data Links, run in the context of a user account. The user account must be a member of the HIS Administrators and HIS Runtime Users Local Groups.  
  
## Folder Access Control List  
 The user account requires the Folder Access Control List settings associated with the HIS Administrators Local Group and HIS Runtime Users Local Group.  
  
 Program Files\Microsoft Host Integration Server 2020  
Program Files\Microsoft Host Integration Server 2020\system  
Program Files\Microsoft Host Integration Server 2020\ SysWOW64  
Program Files\Microsoft Host Integration Server 2020\traces  
Documents\Host Integration Server\Data Sources  
  
## Protection  
  
### Data Tools store the authentication credentials in plain text in the connection string (TXT) file  
 Data Source Wizardstores the authentication credentials (user name and password) in plain text in the connection string text (TXT) file. We recommend that you configure the Data Provider to use Enterprise Single Sign-On (ESSO), which securely stores mappings from Windows Active Directory accounts to IBM host system credentials. The Data Provider retrieves these mappings at runtime to securely authenticate Windows users to remote IBM host file system servers. You should run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### Data Provider connects by using unencrypted, plain text, user name and password  
 Data Provider connects to remote host file system server computers over a TCP/IP or SNA network using basic authentication, where the user name and password are not encrypted and are submitted in plain text. We recommend that you configure the Data Provider to use authentication encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V2.0 when you connect to remote host file system server computers that are running i7/OS.  
  
## Data Provider sends and receives unencrypted data  
 Data Provider sends and receives unencrypted data. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V2.0.  
  
## Data Consumers and Data Tools read and write connection files to and from unsecure folders  
 Data Consumers and Data Tools can read and write connection files to and from unsecure folders. You should store connection string (TXT) files in the Host Integration Server\Data Sources or a program directory, and then secure the folder with local administrator rights. You should store the connection string in the Data Consumer app config file, and then secure the folder with local administrator rights. You should persist the connection information into the Data Consumers and Data Tools secure stores, and then run the Data Provider in-process with the Data Consumer and Data Tools.  
  
## Data Consumers and Data Tools can request connections with invalid properties  
 Data Consumers and Data Tools can request connections with invalid connection property values. You should use the Data Consumers that create connections using the Data Provider connection objects instead of passing unverified connection string argument name value pairs. You should set a connection timeout value to cancel invalid connection attempts.  
  
## Data Consumers and Data Tools can request commands with invalid data  
 Data Consumers and Data Tools can request commands with invalid data. You should use the Data Consumers that create commands using the Data Provider command with parameter objects, to validate parameter types, instead of passing unverified command strings with in-line data values. Data Provider will validate the data based on the metadata schema (HIDX) file. You should set a command timeout value to cancel invalid command attempts.  
  
## Data Consumers and Data Tools read and write metadata files to and from unsecure folders  
 Data Consumers and Data Tools can read and write metadata schema (HIDX) files to and from unsecure folders. You should store metadata HIDX files in the consumer program directory or another directory, and then secure the folder with local administrator rights. Data Provider will verify the metadata HIDX file at connection time. You should set a connection timeout value to cancel invalid connection attempts. You can read/write system-described single record layout IBM i files without using a Data Provider metadata schema (HIDX) file.  
  
## Data Consumers and Data Tools read and write from unsecure local offline data files  
 Data Consumers and Data Tools can read and write from unsecure local offline data files. You should store offline data files in the consumer program directory or another directory, and then secure the folder with local administrator rights.  
  
## See Also  
 [Security and Protection](../core/security-and-protection1.md)
