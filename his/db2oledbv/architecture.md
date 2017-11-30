---
title: "Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 948b4e9e-cf97-4b3d-99d2-037d7086c3b0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Architecture
The Data Provider connects Microsoft SQL Server data consumers to remote IBM DB2 database servers running on a variety of operating systems, including IBM mainframe z/OS and IBM midrange i5/OS. The Data Provider offers cross-platform interoperability capabilities, such as code page conversion and data conversion. The Data Provider offers security and protection features for authentication and data encryption.  
  
## Data Provider  
  
### Data Provider Tools  
 The Data Provider includes tools for use by the IT professional and enterprise developer.  
  
### Data Access Tool with Data Source Wizard  
 The Data Access Tool is a graphical utility for defining, updating, cataloging and using connectivity definitions, in the form of OLE DB Data Link files. From within the Data Access Tool (DAT), you can launch the Data Source Wizard (DSW), which guides you through defining and testing UDL files. The DAT and DSW allow you to test, create DB2 static SQL packages (that contain required CREATE CURSOR statements), change DB2 passwords, and sample query the system catalog table SYSIBM.SYSTABLES.  
  
### Data Links  
 Separately, the OLE DB Data Links graphical utility offers a simpler method of defining and testing UDL files. Most Data Consumers will launch the Data Links tool from within their configuration and deployment tools. The Connection dialog of the Data Links tool includes a Browse button for locating previously-defined UDL files, providing a method to re-use UDL files defined using the DAT and DSW.  
  
### Trace Utility  
 The Data Provider includes a Trace Utility for initiating DB2 network library (client) traces. Also, IT professionals can use Windows Network Monitor to trace DRDA over TCP/IP flows.  
  
## SQL Server Tools  
  
### SQL Server Data Tools (SSDT)  
 SQL Server Data Tools (SSDT) is the primary development environment for creating business solutions using Analysis Services, Integration Services, and Reporting Services. SSDT provides templates, designers, and wizards that are specific to each consumer. 
  
### SQL Server Management Studio  
 SQL Server Management Studio is an integrated environment for accessing, configuring, managing, administering, and developing all components of SQL Server. You can use the graphical tools and script editors in SQL Server Management Studio to work with DB2 data and SQL Server data. In addition, SQL Server Management Studio works with all components of SQL Server such as Reporting Services and Integration Services.  
  
## SQL Server Data Consumers  
  
### Integration Services  
 SQL Server Data Tools (SSDT) provides the Integration Services project in which you create packages, their data sources, and data source views. 
  
### Query Processor  
 Distributed Queries in SQL Server provide distributed concurrent access to multiple data sources. The Distributed Query Processor (DQP) allows you to create heterogeneous queries that join tables in SQL Server with tables in DB2, Host File systems, Oracle, or any other data source accessible by an OLE DB provider. You can use DQP to create SQL Server views over DB2 tables so that developers can write directly to SQL Server and integrate both Windows-based and host-based data in their applications. 
  
### Analysis Services  
 You can use the SSDT to develop Online Analytical Processing (OLAP) cubes and data mining models in SQL Server Analysis Services. This project type includes templates for cubes, dimensions, mining structures, data sources, data source views, and roles, and provides the tools for working with these objects. 
  
### Reporting Services  
 You can use the Report Model and Report Server projects in Business Intelligence Development Studio for developing Reporting Services solutions that access DB2 data. The Report Model project type includes the templates for report models, data sources, and data source views, and provides the tools for working with these objects. The Report Server project includes the templates for working with reports and shared data sources. 
  
### Replication  
 Administrators can move data from SQL Server to DB2 using Replication wizards in SQL Server Management Studio, as part of either snapshot or transactional replication operations. For Replication, SQL Server uses linked servers for connectivity and Integration Services for synchronizing data with DB2.
  
## SQL Server PowerPivot  
 Microsoft SQL Server PowerPivot is self-service BI (Business Intelligence) functionality for users of Microsoft Office. PowerPivot consists of both a client-side component (PowerPivot for Excel) and a server side component (Power Pivot for SharePoint).  
  
### SQL Server PowerPivot for Excel  
 Microsoft PowerPivot for Excel is an add-in that you can use to perform powerful data analysis in Excel, bringing self-service business intelligence to your desktop. PowerPivot for Excel includes a window for adding and preparing data, and a PowerPivot tab on the Excel ribbon that you can use to manipulate the data in an Excel worksheet. 
  
### SQL Server PowerPivot for SharePoint  
 Microsoft SQL Server PowerPivot for SharePoint extends SharePoint and Excel Services to add server-side processing, collaboration, and document management support for the PowerPivot workbooks that you publish to SharePoint. 