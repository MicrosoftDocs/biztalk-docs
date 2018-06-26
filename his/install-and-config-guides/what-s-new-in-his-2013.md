---
title: "What's New in HIS 2013 | Microsoft Docs"
ms.custom: ""
ms.date: 10/24/2016
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 067a6382-eb6e-4d34-880a-0602411032dd
caps.latest.revision: 11
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# What's New in HIS 2013
The following sections in this topic contain information about new features and enhancements in Host Integration Server.  
  
- [Network Integration](../install-and-config-guides/what-s-new-in-his-2013.md#NetworkInteg)  
  
- [Data Integration](../install-and-config-guides/what-s-new-in-his-2013.md#DatIntegration)  
  
- [Application Integration](../install-and-config-guides/what-s-new-in-his-2013.md#AppIntegration)  
  
- [Message Integration](../install-and-config-guides/what-s-new-in-his-2013.md#MessageIntegration)  
  
- [Removed Features](../install-and-config-guides/what-s-new-in-his-2013.md#Removed)  
  
  For more information about all of the features and functionality in Host Integration Server, see [What is HIS](../what-is-his.md).  
  
## Platforms  
  
-   Microsoft Operating Systems  
  
    -   Microsoft Windows® 8.1  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server® 2012 R2  
  
    -   Microsoft Windows Server® 2012  
  
    -   Virtualization with Microsoft Hyper-V®  
  
    -   Virtualization with Microsoft Azure™  
  
-   Microsoft Development Tools and Technologies  
  
    -   Microsoft .NET Framework 4  
  
    -   Microsoft Visual Studio® 2012  
  
-   Microsoft Server Applications  
  
    -   Microsoft SQL Server® 2012  
  
    -   Microsoft BizTalk® Server 2013  
  
-   IBM Operating Systems  
  
    -   IBM z/OS V1.12 and V1.13  
  
    -   IBM zVSE V5.1  
  
    -   IBM i5/OS V7R1  
  
-   IBM Transaction Processing Systems  
  
    -   IBM CICS for z/OS V4.2 and V5.1  
  
    -   IBM IMS V12  
  
    -   IBM i5/OS V7R1  
  
-   IBM Message Processing Systems  
  
    -   IBM WebSphere MQ for z/OS V7.1  
  
-   IBM Relational Database Management Systems  
  
    -   IBM DB2 for z/OS V10  
  
    -   IBM DB2 for i5/OS V7R1  
  
    -   IBM DB2 for LUW V10  
  
    -   IBM Informix IDS V11.7 and V12.1  
  
-   IBM File Systems  
  
    -   IBM DFSMS DFM z/OS V1.12 and V1.13  
  
    -   IBM i5/OS V7R1  
  
##  <a name="NetworkInteg"></a> Network Integration  
  
-   **3270 Emulator**  
  
     Direct connectivity from client to IBM mainframe system over TCP/IP with improved performance and scalability using fully managed TN3270E runtime, supporting authentication and data encryption using Secure Transport Layer Security (TLS) Version 1.0. Host keyboard and color mapper, macro record and playback.  
  
-   **Session Integrator**  
  
     Direct connectivity from server to IBM mainframe system over TCP/IP with improved performance and scalability using fully managed TN3270E runtime, supporting authentication and data encryption using Transport Layer Security (TLS) Version 1.0.  
  
##  <a name="DatIntegration"></a> Data Integration  
  
-   **Server for DB2**  
  
     New Microsoft Service for DRDA supports the Distributed Relational Database Architecture Version 5 protocols and formats as a DRDA Application Server to industry-standard DRA Application Requester clients. The DRDA Server enables IBM DB2 programs to access Microsoft SQL Server 2012 and Microsoft SQL Server 2008 R2 database objects. The DRDA Server converts popular command syntax, most data types, and many encoding schemes to provide a basic compatibility layer between DB2 and SQL Server  
  
-   **Client for DB2**  
  
     Updated Microsoft Client for DB2 supports the Distributed Relational Database Architecture Version 5 protocols and formats as a DRDA Application Requester client to IBM DB2 relational database systems. Now connects to IBM DB2 for z/OS V10, IBM DB2 for i5/OS V7R1, and IBM DB2 for LUW V10.  
  
-   **ODBC Driver for DB2**  
  
     New Microsoft ODBC Driver for DB2 uses the updated Microsoft Client for DB2 to support custom ODBC programs using the Open Database Connectivity Version 3 standard.  
  
-   **OLE DB Provider for DB2**  
  
     Updated Microsoft OLE DB Provider for DB2 uses the updated Microsoft Client for DB2 to support popular COM OLE DB programs such as Microsoft SQL Server 2012 and Microsoft Excel 2013, as well as custom ADO.NET programs using the Microsoft ADO.NET Framework for OLE DB.  
  
-   **ADO.NET Framework Data Provider for DB2**  
  
     Updated Microsoft ADO.NET Framework Data Provider for DB2 uses the updated Microsoft Client for DB2 to support custom ADO.NET programs using the .NET Framework 4.  
  
-   **Client for Informix**  
  
     New Microsoft Client for Informix supports the Distributed Relational Database Architecture Version 5 protocols and formats as a DRDA Application Requester client to IBM Informix IDS V11.7 and V12.1.  
  
-   **OLE DB Provider for Informix**  
  
     New Microsoft OLE DB Provider for Informix uses the new Microsoft Client for Informix to support both popular COM OLE DB programs such as Microsoft SQL Server 2012 and Microsoft Excel 2013, as well as custom ADO.NET programs using the Microsoft ADO.NET Framework for OLE DB.  
  
-   **Client for Host Files**  
  
     Updated Microsoft Client for Host Files supports the Distributed Data Management Record-Level Input/output protocols and formats as a DDM client to IBM host file systems on z/OS and i5/OS. Now supports improved code page and data type conversion using common HIS Encoder. Now connects to IBM DFSMS DFM z/OS V1.12 and V1.13, and IBM i5/OS V7R1.  
  
-   **ADO.NET Framework Data Provider for Host Files**  
  
     Updated Microsoft ADO.NET Framework Data Provider for Host Files uses the updated Microsoft Client for DB2 to support custom ADO.NET programs using the .NET Framework 4.  
  
-   **ADO.NET and BizTalk Adapter Bulk Copy for DB2**  
  
     New ADO.NET and BizTalk Adapter BulkCopy interface instructs the MsDb2Client provider and BizTalk Adapter for DB2 to execute multiple INSERT statements in a batch. Custom ADO.NET applications and Microsoft BizTalk Server Send Port can benefit from increased performance when using the BulkCopy interface.  
  
-   **OLE DB Fast Load for DB2**  
  
     Updated OLE DB DB2OLEDB Session IOpenRowset::FastLoad instructs the managed data provider to execute multiple INSERT statements in a batch. Microsoft SQL Server 2012 Integration Services OLE DB Destination can benefit from increased performance when using the FastLoad interface. Now supports IBM DB2 for z/OS and IBM DB2 for LUW.  
  
-   **Transaction Load Balancing for DB2**  
  
     New transaction load balancing to improve scalability and failover when connecting updated Client for DB2 to remote instances of IBM DB2 for z/OS operating in a data sharing group.  
  
-   **Data Types for DB2**  
  
     New OLE DB Provider for DB2 DBTYPE_NUMERIC mapped to DBTYPE_DECIMAL, for compatibility with OLE DB consumer applications including Microsoft PowerPivot.  
  
     Updated OLE DB Provider for DB2 DBTYPE_TIMESTAMP compatibility with Microsoft SQL Server 2012 and SQL Server 2008 OLE DB consumers applications using datetime2(6).  
  
     Updated OLE DB Provider for DB2 DBTYPE_BYTES and DBTYPE_STR for compatibility with OLE DB command with parameters.  
  
     Updated ADO.NET Framework Data Provider for DB2 MsDb2Type.BLOB and MsDb2Type.CLOB, MsDb2TypeDBCLOB, and MsDb2Type.XML for compatibility with ADO.NET command with parameters.  
  
-   **Connection Pooling for Host Files**  
  
     New client connection pooling to improve scalability and performance when connecting updated Client for Host Files to remote IBM i5/OS via a TCP/IP network connection.  
  
-   **Static SQL Packages for DB2**  
  
     Updated static SQL Packages for DB2 XML file format with associated XSD schema.  
  
-   **Error Documentation for DB2**  
  
     Updated error documentation for DB2, listing common error codes and troubleshooting guidance.  
  
-   **Design Tools for DB2**  
  
     Updated Design Tools for DB2 when running in Microsoft Visual Studio 2012, including support for Server Explorer, Data Set Designer, Query Builder, and Entity Designer.  
  
-   **Long Identifiers for DB2**  
  
     New long identifiers for DB2 when defining and access database objects, including catalog, schema, table, view, procedure, and parameters.  
  
-   **Accounting and Tracing for DB2**  
  
     New session and command source identifiers when connecting to DB2, to enable accounting and improve tracing the Client for DB2. Improved error objects, includes reason code and extended error message.  
  
##  <a name="AppIntegration"></a> Application Integration  
  
-   **TI Client for WCF**  
  
     Added support for WCF Operation Context allowing TI context information (e.g. RE Override) to be sent out-of-band instead of passing the client context as a parameter on the WCF Operation Contract.  The new code gen calling model for WCF allows for programmatic and attribution of WCF options on the Service and Operation contracts.  
  
-   **TI Server for CICS**  
  
     Updated TI server for CICS to support host-initiated connectivity using HTTP.  
  
-   **TI Design Tools**  
  
     Updated TI Designer plug-in for Visual Studio 2012. New C# project templates for popular TI project types.  Metadata repository now persisted in XML as a HIDX (Host Integration data conversion in XML) file.  C# source code now being generated for calling models WCF, Web Service and Direct Call projects improving deployment and custom extensibility scenarios.  Visual Studio Code snippets for commonly used C# and configuration tasks.  Schemas for assisting in the creation of WIP Application / Web configuration files and HIP service configuration files.  
  
-   **TI Client Deployment**  
  
     Updated TI WIP deployment scenarios using web.config and app.config to specify remote environment and configuration metadata.  Updated TI HIP deployment now using service.config to specify HIP service, application and associated metadata.  
  
-   **TI Client and Server Encoding**  
  
     New support for common HIS Encoder (data types, datetime and code page conversions).  
  
-   **TI Accounting**  
  
     New accounting for TI clients.  
  
-   **TI Tracing**  
  
     Transaction Integrator new common HIS tracing infrastructure based on XML configuration files allowing real-time viewing and logging of trace events.  
  
##  <a name="MessageIntegration"></a> Message Integration  
  
-   **Windows Communication Foundation Channel for WebSphere MQ**  
  
     Now supports IBM WebSphere MQ V7.5 or V7.1 (Client, Extended Transactional Client, or Server).  
  
-   **BizTalk Adapter for WebSphere MQ Server**  
  
     Now supports IBM WebSphere MQ V7.5 or V7.1 (Client, Extended Transactional Client, or Server).  
  
##  <a name="Removed"></a> Removed Features  
 The following features have been removed from Host Integration Server.  
  
-   **Microsoft OLE DB Provider for AS/400 and VSAM**  
  
     You should use the Microsoft ADO.NET Framework Data Provider for Host Files or Microsoft BizTalk Adapter for Host Files.  
  
-   **Transaction Integrator TI Manger MMC snap-in administration tool**  
  
     You should use the new TI configuration tool for creating application and web configuration files.  
  
## HIS Community  
 Plug into the Host Integration Server community to connect with other IT professionals and get answers to your questions, read the latest from bloggers, see webcasts, learn about events, and participate in the TechNet Wiki.  
  
|Resource|Location|  
|--------------|--------------|  
|Host Integration Server Home|[http://go.microsoft.com/fwlink/?LinkId=187949](http://go.microsoft.com/fwlink/?LinkId=187949)|  
|Host Integration Server Blog|[http://go.microsoft.com/fwlink/?LinkId=142377](http://go.microsoft.com/fwlink/?LinkId=142377)|  
|Host Integration Server Forum|[http://go.microsoft.com/fwlink/?LinkId=191382](http://go.microsoft.com/fwlink/?LinkId=191382)|  
|TechNet Wiki|[http://go.microsoft.com/fwlink/?LinkId=198099](http://go.microsoft.com/fwlink/?LinkId=198099)|  
  
## Contacting Microsoft About Documentation Issues  
 The Host Integration Server documentation team solicits your feedback about the documentation. Are you finding the information that you need quickly? Are there any gaps in content coverage? Please send your comments and suggestions to us by using the feedback link in the online Help or by contacting us through the Host Integration Server on Microsoft Connect link.  
  
## See Also  
 [What is HIS](../what-is-his.md)   
 [HIS 2013 - What's New, Install, and Configure](../install-and-config-guides/his-2013-what-s-new-install-and-configure.md)