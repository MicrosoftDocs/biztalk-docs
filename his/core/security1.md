---
title: "Security1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99a850c3-75d6-4427-a993-b4a15bbe603e
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Security
The DRDA Service provides cross-platform database access and interoperability through distributed unit of work (DUW) transactions for on-line and batch processing. The DRDA Service connects IBM DB2 DRDA Application Requester client programs to Microsoft SQL Server databases. The DRDA Service functions as an application server supporting the Distributed Relational Database Architecture (DRDA) protocols and formats that are compatible with IBM products functioning as DB2 application requester clients.  
  
 The DRDA Service responds to in-bound DB2 client application requests across Transmission Control Protocol over Internet Protocol (TCP/IP) network connections that use optional security features described in this topic. The DRDA Service initiates out-bound SQL managed client requests using Tabular Data Stream (TDS) using in-memory or TCP/IP network connections.  
  
 The DRDA Service processes in-bound parameterized static SQL commands that the DRDA Service maps to out-bound dynamic SQL CALL statements to execute corresponding SQL Server stored procedures. Also, the DRDA Service processes in-bound dynamic SQL SELECT, INSERT, UPDATE, DELETE and CALL statements as pass-through commands to SQL Server.  
  
 The DRDA Service can authenticate in-bound client requests by mapping user name, user name and password, or Kerberos tickets to Windows credentials. The DRDA Service supports secure authentication and secure data encryption options.  
  
## Windows Security  
  
### Service Account  
 The MsDrdaService.exe must run in the context of a user or service account.  
  
1.  The service account can be the Local System, Local Service, or Network Service account.  
  
2.  The service account can be a local user account.  
  
3.  The service can be a domain user account (Domain\User).  
  
### Local Group  
 The service account must be a member of the HIS Administrators and HIS Runtime Users Local Groups.  
  
1.  The service account must be a member of the HIS Administrators Local Group.  
  
2.  The service account must be a member of the HIS Runtime Users Local Group.  
  
3.  The end user accounts must be a member of the HIS Runtime Users Local Group. For example, when mapping in-bound DRDA AR user name utilizing host-initiated Enterprise Single Sign-On, the mapped Windows user account must be a member of the HIS Runtime Users Local Group.  
  
### Local Security Policy  
 The service account requires these Local Security Policy settings to run as a service.  
  
1. The service account requires Log on as a service.  
  
   The service account requires these Local Security Policy settings to utilize host-initiated Enterprise Single Sign-On.  
  
-   The service account requires Act as part of the operating system.  
  
-   The service account requires Access Credential Manager as a trusted caller.  
  
-   The service account requires Enable computer and user accounts to be trusted for delegation.  
  
### Folder Access Control List  
 The MsDrdaService account requires the Folder Access Control List settings associated with the HIS Administrators Local Group and HIS Runtime Users Local Group.  
  
 The HIS Administrators Local Group has these Folder Access Control settings.  
  
|File Folder|Modify|Read & execute|List folder contents|Read|Write|Special permissions|  
|-----------------|------------|--------------------|--------------------------|----------|-----------|-------------------------|  
|Program Files\Microsoft Host Integration Server 2013||Allow|Allow|Allow|||  
|Program Files\Microsoft Host Integration Server 2013\system||Allow|Allow|Allow|||  
|Program Files\Microsoft Host Integration Server 2013\traces|||||||  
  
 Each user account requires the Folder Access Control List settings associated with the HIS Runtime Users Local Group. For example, each user must have write access to insert lines into a MsDrdaService.DSTF text trace file.  
  
 The HIS Runtime Users Local Group has these Folder Access Control settings.  
  
|File Folder|Modify|Read & execute|List folder contents|Read|Write|Special permissions|  
|-----------------|------------|--------------------|--------------------------|----------|-----------|-------------------------|  
|Program Files\Microsoft Host Integration Server 2013Microsoft Host Integration Server 2013||Allow|Allow|Allow|||  
|Program Files\Microsoft Host Integration Server 2013\system||Allow|Allow|Allow|||  
|Program Files\Microsoft Host Integration Server 2013\traces||Allow|Allow|Allow|Allow||  
  
### ESSO Security Groups  
  
1.  The service account must be a member of the SSO Affiliate Administrators Local Group.  
  
2.  The service account may be a member of the SSO Administrators Local Group.  
  
### Constrained Delegation and Kerberos  
 ESSO requires elevated permissions in Active Directory (Kerberos constrained delegation, and Use any authentication protocol). ESSO requires a Kerberos Service Principal Name for the SQL Server computer to which the DRDA Service connects.