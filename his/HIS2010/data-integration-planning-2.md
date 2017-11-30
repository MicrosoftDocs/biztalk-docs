---
title: "Data Integration (Planning)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33a8b04e-060c-4a08-97dc-76d8e2bbcf8c
caps.latest.revision: 8
---
# Data Integration (Planning)
Enterprise IT organizations need to deliver new solutions that extend investments in existing IBM systems and data stores. Microsoft Host Integration Server 2010 offers technologies and tools to enable IT professionals, enterprise developers and knowledge workers to access and integrate vital information stored in IBM DB2 relational database management systems and record-oriented host file systems. The following table describes the supported platforms and versions.  
  
## Data Sources  
  
|||  
|-|-|  
|**Data Source**|**Platform and Version**|  
|DB2|IBM DB2 for z/OS V8.1 and DB2 for z/OS V9.1<br /><br /> IBM DB2 for i5/OS V5R4, V6R1 and V7R1<br /><br /> IBM DB2 UDB for Windows, AIX, HP-UX, Solaris, Linux V9.1, V9.5, V9.7|  
|Host Files|IBM DFSMS DFM z/OS V1.9, V1.10, V1.11 and V1.12<br /><br /> IBM i5/OS V5R4, V6R1 and V7R1|  
  
 The HIS 2010 data integration technologies and tools use IBM and industry-standard protocols and formats to help you connect to the back end data sources. The common IBM architecture is Distributed Data Management (DDM), which IBM has built into its DB2 servers and its mainframe z/OS and midrange i5/OS file systems.  
  
## Data Integration Architectures, Providers and Consumers  
 When accessing remote IBM DB2 database servers, Microsoft technologies operate as industry-standard Distributed Relational Database Architecture (DRDA) Application Requester (AR) clients. To connect to IBM file systems (Host Files), Microsoft technologies operate as IBM-standard Record-Level Input/Output (RLIO) clients. On top of these network clients, HIS 2010 offers a set of data provider features for you to use. The following table describes providers, architecture and consumers.  
  
||||  
|-|-|-|  
|**Provider**|**Architecture**|**Consumers**|  
|ADO.NET Provider for DB2|.NET Framework|Win Forms, Web Forms, Web Services, SQL Server Integration Services|  
|Entity Provider for DB2|Entity Framework|Entity Data Model, WCF Data Services|  
|BizTalk Adapter for DB2|BizTalk Messaging|BizTalk Server|  
|OLE DB Provider for DB2|Component Object Model|Office Excel, SharePoint, SQL Server (Integration Services, Analysis Services, Reporting Services, Replication Services, and Query Processor), SQL Server PowerPivot for Excel, SQL Server PowerPivot for SharePoint|  
|ADO.NET Provider for Host Files|.NET Framework|Win Forms, Web Forms, Web Services, SQL Server Integration Services|  
|BizTalk Adapter for Host Files|BizTalk Server|BizTalk Server|  
|OLE DB Provider for AS/400 and VSAM|Component Object Model|Office Excel, SharePoint, SQL Server Integration Services and Query Processor|  
  
## Data Consumer Tools  
 When you want to define and manage connections, configure or develop applications, Microsoft offers the set of technologies described in the following table.  
  
||||  
|-|-|-|  
|**Product**|**Tool**|**Description**|  
|HIS|Data Access Tool with Data Source Wizard|HIS Data Access Tool with Data Source Wizard guides the knowledge worker, IT professional or enterprise developer to define and manage connections to DB2 and host files.|  
|HIS|Data Access Library|HIS Data Access Library offers a set of .NET Framework 3.51 components to automate common data administration tasks, such as defining connections and creating static SQL packages for DB2.|  
|Visual Studio|VS Server Explorer, Query and View Designer, DataSet Designer with TableAdapter Wizard|VS Server Explorer, Query and View Designer, DataSet Designer with TableAdapter Wizard assist the enterprise developer to develop Windows Form, XML Web Service and Web Form applications with less ADO.NET provider coding required.|  
|SharePoint|Data Sources in SharePoint Designer|SharePoint Designer enables IT professionals to integrate DB2 and host file system data with collaboration and business intelligence Web sites|  
|SQL Server|SQL Server Management Studio and Business Intelligence Development Studio|SQL Server Management Studio and Business Intelligence Development Studio enable the IT professional and enterprise developer to deliver data.|  
|Excel and SharePoint|SQL Server PowerPivot Add-in for Excel and SQL Server Reporting Services Report Builder|SQL Server PowerPivot Add-in for Excel and SQL Server Reporting Services Report Builder enable self-serve business intelligence for streamlining the integration of data from multiple sources.|  
|BizTalk Server|BizTalk Administrator and BizTalk Explorer|BizTalk Adapters are based on the Microsoft ADO.NET Data Providers for DB2 and Host Files, offering intuitive wizards to configure the static solicit and response send ports solutions that efficiently integrate DB2 databases without writing code.|  
|Visual Studio|Entity Designer|VS Entity Designer, based on the Entity Framework and Entity Data Model, enables enterprise developers to connect DB2 data through Language Integrated Query (LINQ) and ADO.NET Data Services.|  
  
## Data Command Syntax  
 Microsoft HIS 2010 data providers support a set of access methods and command syntax, depending on the data source and provider architecture. The following table describes the supported providers, command types and command syntax.  
  
||||  
|-|-|-|  
|**Provider**|**Command Types**|**Command Syntax**|  
|ADO.NET Provider for DB2|Dynamic SQL, Static SQL, Stored Procedures|ANSI SQL 92 Entry-level syntax supported by IBM DB2 servers|  
|Entity Provider for DB2|Dynamic SQL, Stored Procedures|ANSI SQL 92 Entry-level syntax supported by IBM DB2 servers|  
|BizTalk Adapter for DB2|Dynamic SQL, Stored Procedures|Subset of ANSI SQL 92 Entry-level syntax, specific to HIS data provider (**SELECT**, **INSERT**, **UPDATE**, **DELETE**, **CALL**)|  
|OLE DB Provider for DB2|Dynamic SQL, Stored Procedures|ANSI SQL 92 Entry-level syntax supported by IBM DB2 servers|  
|ADO.NET Provider for Host Files|Sequential, Keyed, Relative Record|Subset of ANSI SQL 92 Entry-level syntax, specific to HIS data provider (**SELECT**, **INSERT**, **UPDATE**, **DELETE**)|  
|BizTalk Adapter for Host Files|Sequential, Keyed, Relative Record|Subset of ANSI SQL 92 Entry-level syntax, specific to HIS data provider (**SELECT**, **INSERT**, **UPDATE**, **DELETE**)|  
|OLE DB Provider for AS/400 and VSAM|Sequential, Keyed, Relative Record, Remote Command (i5/OS)|Specific to HIS data provider (**EXEC OPEN**, **EXEC COMMAND**)|  
  
## Host File Access Methods  
 Microsoft data providers for host files support multiple access methods, data set types, and record types, depending on the back end data source platform.  
  
||||  
|-|-|-|  
|**Platform**|**Access Method**|**Data Set Type**|  
|Mainframe (z/OS)|Sequential Access Method (SAM)|Basic Sequential Access Method (BSAM) data sets|  
|||Queued Sequential Access Method (QSAM) data sets|  
||Virtual Storage Access Method (VSAM)|Entry-Sequenced Data Sets (ESDSs)|  
|||Key-Sequenced Data Sets (KSDSs)|  
|||Fixed-length Relative Record Data Sets (RRDSs)|  
|||Variable-length Relative Record Data Sets (VRRDSs)|  
|||VSAM Alternate Indexes to ESDSs or KSDSs|  
||Basic Partitioned Access Method|Partitioned Data Sets (PDS) and Partitioned Data Set Extended (PDSE) directories and members|  
|Midrange (i5/OS)|Sequential and Keyed Access|Single and multiple member Physical files (PF) and Keyed physical files (KPF)|  
|||Logical files (LF) over a PF or KPF|  
  
## OLE DB Provider for DB2 with SQL Server 2008 R2  
 SQL Server 2008 R2 provides a rich array of tools that you can use to create DB2 solutions with SQL Server consumers.  
  
 **Business Intelligence Development Studio**  
  
 Business Intelligence Development Studio is the primary development environment that you can use for creating business solutions using Analysis Services, Integration Services, and Reporting Services. Business Intelligence Development Studio provides templates, designers, tools, and wizards that you can use which are specific to each consumer. For more information, see [Introducing Business Intelligence Development Studio](http://go.microsoft.com/fwlink/?LinkID=180755) (http://go.microsoft.com/fwlink/?LinkID=180755).  
  
 **SQL Server Management Studio**  
  
 SQL Server Management Studio is an integrated environment that you can use for accessing, configuring, managing, administering, and developing all components of SQL Server. You can use the graphical tools and script editors in SQL Server Management Studio to work with DB2 data and SQL Server data. In addition, SQL Server Management Studio works with all components of SQL Server such as Reporting Services and Integration Services. For more information, see [Using SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkID=180759) (http://go.microsoft.com/fwlink/?LinkID=180759).  
  
 **Integration Services**  
  
 You can use the Integration Services project type in Business Intelligence Development Studio to create data extraction, transformation, and loading (ETL) applications. It contains templates for packages, data sources, and data source views, and provides the tools for working with these objects. For more information, see [Integration Services](http://go.microsoft.com/fwlink/?LinkID=180757) in Business Intelligence Development Studio (http://go.microsoft.com/fwlink/?LinkID=180757). You can also use the Namespaces in the [http://go.microsoft.com/fwlink/?LinkID=180760](http://go.microsoft.com/fwlink/?LinkID=180760) (http://go.microsoft.com/fwlink/?LinkID=180760) to programmatically create and manage packages. For more information about how to create Integration Services solutions, see the [Integration Services Developer InfoCenter](http://go.microsoft.com/fwlink/?LinkID=180761) (http://go.microsoft.com/fwlink/?LinkID=180761). For more information about SQL Server Integration Services, see [SQL Server Integration Services](http://go.microsoft.com/fwlink/?LinkID=180424) (http://go.microsoft.com/fwlink/?LinkID=180424).  
  
 **Analysis Services**  
  
 You can use the Business Intelligence Development Studio to develop Online Analytical Processing (OLAP) cubes and data mining models in SQL Server Analysis Services. This project type includes templates for cubes, dimensions, mining structures, data sources, data source views, and roles, and provides the tools for working with these objects. For more information, see [Analysis Services in Business Intelligence Development Studio](http://go.microsoft.com/fwlink/?LinkID=180756) (http://go.microsoft.com/fwlink/?LinkID=180756). For the Analysis Services documentation, see [SQL Server Analysis Services - Multidimensional Data](http://go.microsoft.com/fwlink/?LinkID=180426) (http://go.microsoft.com/fwlink/?LinkID=180426) and [SQL Server Analysis Services - Data Mining](http://go.microsoft.com/fwlink/?LinkID=180427) (http://go.microsoft.com/fwlink/?LinkID=180427).  
  
 **Reporting Services**  
  
 You can use the Report Model and Report Server projects in Business Intelligence Development Studio for developing Reporting Services solutions that access DB2 data. The Report Model project type includes templates for report models, data sources, and data source views for you to use, and provides the tools you need for working with these objects. The Report Server project includes the templates you can use for working with reports and shared data sources. For more information, see Reporting Services in [Business Intelligence Development Studio](http://go.microsoft.com/fwlink/?LinkID=180758) (http://go.microsoft.com/fwlink/?LinkID=180758). For the Reporting Services documentation, see [SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkID=180428) (http://go.microsoft.com/fwlink/?LinkID=180428).  
  
 **Replication**  
  
 Administrators can move data from SQL Server to DB2 by using Replication wizards in SQL Server Management Studio, as part of either snapshot or transactional replication operations. For Replication, SQL Server uses linked servers for connectivity and Integration Services for synchronizing data with DB2. For the SQL Server Replication documentation, see [SQL Server Replication](http://go.microsoft.com/fwlink/?LinkID=180425) (http://go.microsoft.com/fwlink/?LinkID=180425).  
  
 **Query Processor**  
  
 Administrators and developers can use distributed queries to access data from multiple heterogeneous data sources including DB2. For more information about how to configure DB2 data sources, see Connectivity and Data Access. For more information about SQL Server distributed queries, see [Distributed Queries](http://go.microsoft.com/fwlink/?LinkID=180429) (http://go.microsoft.com/fwlink/?LinkID=180429).  
  
## Entity Provider for DB2 with Entity Data Model  
 Enterprise developers need to extend existing data storage systems, integrating valuable information more efficiently in new applications, without requiring changes to the underlying data store. Microsoft ADO.NET Data Services and Entity Data Model (EDM) provide the data architecture components and tools to enable enterprise developers to deliver new solutions faster, while retaining the data integrity and security of enterprise data stores. Data services provide an isolation layer between the physical data in the data store and the logical data used by applications. Modeling provides a way to work on the information with context associated with a given data-aware application or set of applications.  
  
 With the ADO.NET Entity Framework and Microsoft Entity Provider for DB2, which sits on top of the Microsoft ADO.NET Provider for DB2, enterprise developers can create data access applications by programming against a conceptual application model instead of programming directly against the DB2 storage schema. Using EDM with the Entity Provider for DB2, enterprise developers can deliver solutions faster, while decreasing the amount of code and maintenance required for data-aware applications.  
  
## Data Access Library  
 The Data Access Library (DAL) offers .NET Framework 3.51 components and interfaces to automate common administrative tasks, such as defining connections, changing passwords, creating standard and customer packages.  
  
 Creating Connections for DB2  
  
 Creating Connections for Host Files  
  
 Creating Standard Packages for DB2  
  
 Creating Custom Packages for DB2  
  
 Changing Passwords for DB2  
  
 Additionally, the HIS 2010 Data Access Tool and Data Source Wizard utilize the Data Access Library as underlying technology, to connect these tools to the Microsoft network clients and data providers at runtime. For example, when using the Data Source Wizard to test a connection, the Data Source Wizard connects via the Data Access Library to the Microsoft network client for DB2.  
  
 For more information, see [Data Access Library Tasks](../HIS2010/data-access-library-tasks2.md) in [Data Integration (Configuration)](../HIS2010/data-integration-configuration-1.md) and the <xref:Microsoft.HostIntegration.DataAccessLibrary> Namespace documentation.  
  
## See Also  
 [Supported Data Integration Programming Scenarios](../HIS2010/supported-data-integration-programming-scenarios.md)   
 [Data Integration (Planning)](../HIS2010/data-integration-planning-2.md)