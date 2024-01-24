---
description: "Learn more about: Security Features in the Data Provider for Informix"
title: "Security Features in the Data Provider for Informix"
ms.custom: ""
ms.date: "07/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security Features in the Data Provider for Informix
You can use the OLE DB Provider for Informix (Data Provider) to connect Windows data consumer applications to remote IBM Informix relational database management servers. The Data Provider function as a distributed relational database architecture (DRDA) application requester client that supports the DRDA protocol and formats that are compatible with IBM Informix server products functioning as DRDA application servers.  
  
 You can use the Data Provider by issuing structured query language statements. These statements include data definition language statements for administration and data manipulation management statements for read and write operations. The Data Provider connects the Windows client applications to the Informix server databases across a transmission control protocol over an Internet protocol (TCP/IP) network that use one or more of the optional security features described later in this topic.  
  
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
  
### Data Tools store the authentication credentials in plain text in the Universal Data Link (UDL)  
 Data Links stores the authentication credentials (user name and password) in plain text in the Universal Data Link (UDL) file. We recommend that you configure the data providers to use Enterprise Single Sign-On (ESSO), which securely stores mappings from Windows Active Directory accounts to IBM Informix credentials. The data providers retrieve these mappings at runtime to securely authenticate Windows users to remote IBM Informix database servers. You should run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### Data Provider connects by using unencrypted, plain text, user name and password  
 Data Provider connects to remote Informix server computers over a TCP/IP network using basic authentication, where the user name and password are not encrypted and are submitted in plain text. We recommend that you configure the Data Provider to use authentication encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V2.0.  
  
### Data Provider sends and receive unencrypted data  
 Data Provider sends and receives unencrypted data. We recommend that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V2.0.  
  
### Data Consumers and Data Tools read and write connection files to and from unsecure folders  
 Data Consumers and Data Tools can read and write connection files to and from unsecure folders. You should store Universal Data Link (UDL) files in the Host Integration Server\Data Sources or a program directory, and then secure the folder with local administrator rights. You should persist the connection information into the Data Consumers and Data Tools secure stores, and then run the Data Provider in-process with the Data Consumer and Data Tools.  
  
### Data Consumers and Data Tools can request connections with invalid properties  
 Data Consumers and Data Tools can request connections with invalid connection property values. You should use the Data Consumers that create connections using the Data Provider connection objects instead of passing unverified connection string argument name value pairs. You should set a connection timeout value to cancel invalid connection attempts.  
  
### Data Consumers and Data Tools can request commands with invalid data  
 Data Consumers and Data Tools can request commands with invalid data. You should use the Data Consumers that create commands using the Data Provider command with parameter objects, to validate parameter types, instead of passing unverified command strings with in-line data values. You should set a command timeout value to cancel invalid command attempts. . You should set a command timeout value to cancel invalid command attempts. You should use DRDA distributed unit of work (DUW), instead of remote unit of work (RUW), to protect the Data Consumers using two-phase commit transactions.
