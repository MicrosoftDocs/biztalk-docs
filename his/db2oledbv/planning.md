---
title: "Planning | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46b7553b-f88a-458c-9873-b3a0bc192654
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Planning
Enterprise developers who are using on-line transactional processing (OLTP) and business intelligence (BI) technologies can take advantage of the SQL Server data access architecture to connect IBM DB2 databases to new solutions built by using SQL Server integration, analysis, reporting, replication and distributed query technologies. The Data Provider supports SQL commands. This allows for interoperability between COM OLE DB-enabled consumer services and tools in Microsoft SQL Server and remote IBM DB2 relational database management systems. You can execute data definition language (DDL) or data manipulation language (DML) SQL statements that include read and write operations based on dynamic SQL in addition to stored procedures within remote unit of work (RUW) transactions.  
  
## Planning   
  
### Data Provider  
 Microsoft OLE DB Provider for DB2 (Data Provider) allows IT professionals and enterprise developers using Microsoft SQL Server technologies and tools to access, read, and write vital information stored in IBM DB2 relational database management systems. The Data Provider connects to DB2 using an underlying Microsoft network client for DB2 that functions as a DB2 DRDA Application Requester.  
  
### DB2 Servers  
 You can use the Data Provider to interact with IBM DB2 database servers on the following platforms using a DRDA over TCP/IP network connection.  
  
### SQL Server Products  
 The Data Provider is compatible with Microsoft SQL Server software products as OLE DB data consumers. The Data Provider must be installed on the same computer as the Microsoft SQL Server software product for use in-process with the Data Consumer application.  
  
### SQL Server Data Tools (SSDT)  
 SQL Server Data Tools (SSDT) SDT include special project types and tools for developing SQL Server Analysis Services, Reporting Services, and Integration Services Business Intelligence (BI) solutions (formerly known as Business Intelligence Development Studio). SSDT interact indirectly with the Data Provider through the SQL Server Data Consumers.   
  
### SQL Server Data Consumers  
 SQL Server Integration Services, SQL Server Analysis Services, and SQL Server Reporting Services interact indirectly with the Data Provider through the Microsoft ADO.NET Data Provider for OLE DB. Distributed query processing interacts with the Data Provider directly through OLE DB. SQL Server Replication requires a DQP-defined linked server for specifying the initial connectivity information, but will use ADO.NET to OLE DB integration at run time when synchronizing data. SQL Server provides a rich array of tools that you can use to create DB2 solutions with SQL Server consumers.  
  
### SQL Server PowerPivot  
 Microsoft SQL Server PowerPivot is self-service BI (Business Intelligence) functionality for users of Microsoft Office. PowerPivot consists of both a client-side component (PowerPivot for Excel) and a server side component (Power Pivot for SharePoint). SQL Server PowerPivot interacts directly with the Data Provider to access information stored in DB2 databases.  
  
### Data Conversion  
 The Data Provider converts to and from DRDA formatted data types and OLE DB data types. Depending on the SQL Server Consumer, IT professionals can control the conversion using an XML data type mapping configuration file or SQL Server data type mapping system table.  
  
### Code Page Conversion  
 Organizations often have to develop solutions that are globalized for deployment in multiple locales. IT professionals can configure the Data Provider to process string conversions based on standard Coded Character Set Identifiers (CCSIDs) and code pages, including support for single-byte, mixed-byte, double-byte, EBCDIC, ANSI, OEM PC, UNICODE, Arabic and Hebrew bi-directional layout conversion.  
  
### Security  
 Enterprise IT organizations seek ways to secure the authentication credentials and user data that flows across the network. The Data Provider offers technologies for authentication encryption, data encryption, or both authentication and data encryption. IT professionals can configure the Data Provider to use 256-bit Advanced Encryption Standard (AES) to secure the authentication credentials, as well as 56-bit Data Encryption Standard (DES) to secure both the authentication credentials and user data. At the TCP/IP network layer, the Data Provider supports either Secure Sockets Layer (Version 3.0) or Transport Layer Security (TLS Version 1.0 and 1.2) to encrypt both authentication credentials and user data. The Data Provider supports optional use of Enterprise Single Sign-On Version 5 to map foreign credentials (e.g. RACF Username) to Windows Active directory credentials. ESSO is a separately installable feature of Microsoft Host Integration Server licensed as supplemental technology to Microsoft BizTalk Server.
 
### Usage reporting 
 Data Provider includes technology for telemetry and error reporting. The HIS product team utilizes this data to improve the quality, reliability, and performance of the Data Provider. Ths includes:
- Installation reports when product is installed, changed or removed.
- Runtime monitors connections established by reporting the connection instance by DRDA server class and version, data provider name and data consumer process name.
- Runtime monitors errors by reporting SQLSTATE, SQLCODE, and reason code.

  > **NOTE:** To disable usage reporting, use the **Options** dialog of the Data Provider **Data Access Tool**. 