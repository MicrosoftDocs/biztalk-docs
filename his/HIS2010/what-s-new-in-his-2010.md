---
title: "What&#39;s New in HIS 2010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdc0f42d-8e81-4494-bff7-87365c6408ea
caps.latest.revision: 29
---
# What&#39;s New in HIS 2010
The following sections in this topic contain information about new features and enhancements in Microsoft Host Integration Server 2010.  
  
-   [Network Integration](../HIS2010/what-s-new-in-his-2010.md#NetworkInteg)  
  
-   [Data Integration](../HIS2010/what-s-new-in-his-2010.md#DatIntegration)  
  
-   [Application Integration](../HIS2010/what-s-new-in-his-2010.md#AppIntegration)  
  
-   [Message Integration](../HIS2010/what-s-new-in-his-2010.md#MessageIntegration)  
  
-   [Removed Features](../HIS2010/what-s-new-in-his-2010.md#Removed)  
  
 For more information about all of the features and functionality in Host Integration Server 2010, see [Overview of HIS 2010](../HIS2010/overview-of-his-2010.md).  
  
##  <a name="NetworkInteg"></a> Network Integration  
  
-   **IPv6 Transport for SNA Clients and Servers**  
  
     Enterprise organizations are increasing the number of desktops, devices, and servers that are connecting across a TCP/IP network infrastructure. To improve addressability and manageability of these networks, HIS 2010 offers support for new Internet Protocol Version 6 (IPv6) and existing IPv4 configurations. IT professionals can deploy HIS clients and HIS servers into IPv6-only, IPv4-only, or mixed environments, whether connecting client-to-server, server-to-server, or server-to-host using HPR/IP.  
  
-   **Session Integrator Authentication and Data Encryption using TLS**  
  
     Some enterprise have standardized on TCP/IP and use TN3270 when the system connects clients and server workloads to IBM mainframe z/OS computers. Previously, HIS offered Session Integrator connectivity over both SNA LU2 using HPR/IP and TN3270 using TCP/IP. In HIS 2010, developers can improve the security of solutions that are based on Session Integrator, by configuring 3270 sessions to authentication and data encryption based on Transport Layer Security (TLS) V1.0.You can improve security by encrypting authentication credentials and data by using Secure Transport Layer Security (TLS) V1.0 when you connect to IBM mainframe systems using Session Integrator TN3270 transport across a TCP/IP network connection.  
  
##  <a name="DatIntegration"></a> Data Integration  
  
-   **DB2 and Host Files Enhanced Security using AES, SSL and TLS**  
  
     The HIS 2010 data providers for DB2 and host files use industry-standard distributed data management (DDM) protocols and formats. By default, the distributed relational database architecture (DRDA) and record-level input/output (RLIO) formats are unencrypted, exposing the information and creating a security threat to the organization. Enterprise IT organizations seek ways to secure the authentication credentials and user data that flows across the network. In HIS 2010, the data providers for DB2 and host files offer technologies for authentication encryption, data encryption, or both authentication and data encryption. When connecting to DB2 servers across an SNA APPC using HPR/IP network connection, IT professionals can configure the data providers to use 256-bit Advanced Encryption Standard (AES) to secure the authentication credentials. When connecting to IBM DB2 servers across a TCP/IP network connection, the data providers can use either Secure Sockets Layer (Version 3.0) or Transport Layer Security (TLS Version 1.0) to encrypt both authentication credentials and user data. When connecting to i5/OS host file servers across a TCP/IP network connection, the data providers can use either 128-bit Secure Sockets Layer (Version 3.0) or Transport Layer Security (TLS Version 1.0) to encrypt both authentication credentials and user data.  
  
-   **DB2 Improved Connection Pooling**  
  
     The data providers for DB2 support their own provider connection pooling to improve performance by reusing connections. Previously, connection pooling was restricted for use with remote unit of work connections (RUW) where the connection parameters matched exactly. In HIS 2010, IT professionals can use client-side connection pooling with both distributed unit of work (DUW) and RUW. Also, IT professionals can use client-side connection pooling even when some configuration parameters do not match. This includes connection properties that define specific end users, workstations and applications (client accounting, client application name, client user identifier, client workstation name).  
  
-   **DB2 Large Object Data Types**  
  
     Enterprise developers store important information in binary large objects (BLOB) and character large objects (CLOB). Commonly, BLOB and CLOB are used to store images and text for a range of documents. This includes component manufacturing specifications and retail product catalogs. Using the OLE DB Provider for DB2, developers can read BLOB and CLOB data by using SELECT and CALL statements from OLE DB consumers, such as SQL Server Integration Services, Analysis Services, Reporting Services and Distributed Query Processor.  
  
-   **DB2 Static SQL Package Bind Options**  
  
     Many enterprise developers use static SQL packages to optimize access to DB2 servers. Static SQL offers improved performance and security, compared to dynamic SQL. When using DB2 static SQL, you can improve compatibility and security by specifying additional package bind (creation) options. In HIS 2010, developers can specify package-level defaults for locales (code pages, datetime formats, string and decimal delimiters), security (authorization levels), and transactions (isolation levels, commit and statement preparation keep).  
  
-   **BizTalk Adapter for DB2 Multiple Table Update**  
  
     To integration line-of-business systems across the enterprise, IT professionals deploy BizTalk Server, which offers efficient XML document interchange and flexible business process orchestration. Previously, when using the BizTalk Adapter for DB2 to update (**INSERT**, **UPDATE**, **DELETE**, or **CALL**) rows across multiple DB2 tables, developers had to use separate XML documents, which required use of additional pipeline processing to disassemble XML documents before submitting them to the adapter send port. In HIS 2010, developers can use a single XML document instance to reference multiple DB2 tables, improving scalability and performance, while allowing for greater flexibility in specifying batches and transactions scope.  
  
-   **Host Files Offline Writer**  
  
     HIS developers use the ADO.NET Provider for Host Files to access and integrate information stored in existing host record-oriented files with new solutions that are based on the .NET Framework. When accessing information stored in z/OS host file systems, the data provider must connect across an SNA APPC session using high performance routing over internet protocol (HPR/IP) network. Some enterprises have standardized on TCP/IP and cannot upgrade their host systems to support HPR/IP. Previously, HIS offered an improved host file provider that supports off-line reading of binary files, which allowed for use of file transfer protocol (FTP) as a means to read host data without an SNA APPC session. However, there was no solution for writing data back to the host system. In HIS 2010, the enhanced host file provider supports off-line writing to binary files. This enables enterprise developers to read and write host data without a live connection to the host file system. When operating in off-line reader/writer mode, the ADO.NET Data Provider supports the same record access methods (sequential, keyed, and combined) and record formats based on local metadata produced by the host file designer for Visual Studio.  
  
-   **Host Files Developer Tools**  
  
     When integrating information stored in host file systems, enterprise developers will use the ADO.NET Data Provider for Host Files and BizTalk Adapter for Host Files. Developers can define connections using the Data Source Wizard in the Data Access Tool or Visual Studio Server Explorer (Data Connections). Previously, HIS did not let developers define and test connections to host files from Visual Studio running on Windows X64 operating systems. In HIS2010, developers can add Data Connections to host files and test these using the Query Builder from Visual Studio running on Windows X64 operating systems. This increases efficiency by reducing the need for additional operating systems or virtualized environments.  
  
     To read and write records in host files, the ADO.NET Provider for Host Files and BizTalk Adapter for Host Files used a host data conversion runtime that relies on a local metadata schema file (.NET assembly). Developers had a choice of manually-defining the schema or generating a metadata assembly by importing host source code. The COBOL and RPG import wizard required a good deal of COBOL or RPG knowledge. In HIS 2010, the import wizard has been enhanced to offer an automatic mode. This allows developers with little or no knowledge of COBOL or RPG to generate metadata assemblies. Host files frequently contain many columns with complex conversions (REDEFINE, OCCURS, REDEFINE). In HIS 2010, the importers have been enhanced to improve performance when parsing large and complex source files. After importing the source file, the enhanced Host Files Designer now provides a list of warnings and errors. The developer can now double-click an issue item to jump to that part of the schema in the metadata assembly by collapsing or expanding the definition to improve usability.  
  
     To convert records in host files by using the OLE DB Provider for AS/400 and VSAM, developers must define a Host Column Description (HCD) file. In HIS 2010, the Host Files Designer replaces the Data Access Tool for defining or editing HCDs. The Host Files Designer can create, import, and save HCD files.  
  
-   **DB2 Multi Row Input**  
  
     Many enterprises use SQL Server as a data storage platform for new application workloads. IT organizations must connect SQL Server to existing data stores that include IBM DB2 relational database servers. As the amount of information stored in SQL Server increases, IT professionals seek new technologies to increase throughput when moving data from SQL Server to DB2. In HIS 2010, the OLE DB Provider for DB2 has been enhanced to include an IRowsetFastLoad interface. This allows increased performance and scalability when it sends information to DB2. Using the SSIS package designer in the Visual Studio Business Intelligence Design Studio, enterprise developers can configure OLE DB destinations in a data flow to use IRowsetFastLoad. This instructs the data provider to execute multiple **INSERT**, **UPDATE**, **DELETE** or **CALL** statements in a batch to more efficiently use TCP/IP network packages and increase overall performance.  
  
-   **DB2 Data Conversion**  
  
     Organizations often have to develop solutions that are globalized for deployment in multiple locales. Previously, HIS offered data conversion that supported multiple coded character set identifiers. This included support for double-byte and mixed byte, to support a broad range of locales. A common problem across Arabic and Hebrew locales is the storage layout, which is reversed on heritage IBM systems (z/OS and i5/OS store data in visual order) when compared to Windows operating systems (store data in logical order). In HIS 2010, the data providers for DB2 and host files have been enhanced to support Hebrew bi-directional layout conversion. This allows enterprise developers to automatically convert character data that is encoded in IBM EBCDIC Hebrew code page 424. Another common problem across all locales is the emergence of larger integer values. In HIS 2010, the data providers for DB2 support the BIGINT data type. This allows for modernization of applications across both Windows operating systems and host systems.  
  
##  <a name="AppIntegration"></a> Application Integration  
  
-   **Authentication and Data Encryption using SSL and TLS**  
  
     Enterprise IT organizations are consolidating network infrastructure by using a combination of TCP/IP and HPR/IP. Previously, IT professionals relied on IPSec to secure network connections used by Transaction Integrator and BizTalk Adapter for Host Applications. In HIS 2010, developers can define connections that encrypt authentication credentials and user data by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 when connecting via TCP/IP to IBM Information Management System (IMS) for z/OS or IBM i5/OS programs.  
  
-   **Enhanced HTTP Transport for CICS**  
  
     Customer Information Control System (CICS) offers enhanced connectivity using industry-standard hypertext transport protocol (HTTP). Previously, HIS offered TI and BizTalk adapter connectivity to CICS via HTTP. In HIS 2010, developers have more options when they use HTTP to CICS. This includes support for both z/OS and z/VSE. To improve usability and offer the greatest compatibility, developers can now use the well-known CICS LINK programming model. For more flexibility, developers can use the User Data programming model when they connect to CICS via HTTP. To reduce session startup time or allow for long-running transactions, developers can use persistent connections.  
  
-   **BizTalk Adapter for Host Applications Dynamic Remote Environments**  
  
     BizTalk Adapter for Host Applications offers you more flexibility in deployment and runtime by offering Dynamic Remote Environments. You can specify remote environment definitions in the send port, instead of relying on static remote environments that are pre-defined by using the TI Manager MMC snap-in.  
  
-   **Transaction Integrator support for Edited Numerics**  
  
     You can convert to and from COBOL edited numeric data types to maintain compatibility with existing programs that use this format structure. This support improves understanding, readability, and printing of numeric data values.  
  
-   **Improved Development Tools**  
  
     The TI Designer has been enhanced to offer a more intuitive import wizard, which provides beginners with a simplified import process while retaining the optional advanced mode for experienced developers. Developers can use the improved output dialog to list warnings and errors which supports double-clicking to navigate to the problem node. To traverse large and complex assemblies, TI Designer lets you expand and contract nodes.  
  
     In earlier versions of HIS, developers could use the Simulator Host feature to execute programs off-line, based on the pre-defined HIS tutorial samples or installation verification tests. In HIS 2010, when connecting to a live system is not possible, the Host Simulator can emulate workloads for use with Transaction Integrator and BizTalk Adapters for Host Applications. Host Simulator replaces the old tool, providing pre-defined listeners for the tutorials and IVTs. When you are ready to move beyond the pre-defined programs, Host Simulator lets you define your own programs to execute TI workloads with a live host connection.  
  
##  <a name="MessageIntegration"></a> Message Integration  
  
-   **WCF Channel for WebSphere MQ**  
  
     Many enterprises are developing new solutions that are based on Windows Communications Foundation, which is a part of the .NET Framework that provides a unified programming model for quickly building service-oriented applications across the Web and the enterprise. At the same time, IT organizations rely on existing messaging infrastructure in the form of IBM WebSphere MQ. Previously, HIS offered a WCF Channel for WebSphere MQ. In HIS 2010, the WCF Channel has been enhanced to take advantage of.NET Framework 4.  
  
     To improve reliability, developers can use the receive context functionality in a queued WCF channel for WebSphere MQ to lock a message before processing it. If a failure occurs, the message remains locked so that the service can appropriately respond to the failure. When working with a one-way WCF Channel for WebSphere MQ, receive context allows a service to control when it sends an acknowledgement message or it can indicate a problem by sending a negative acknowledgement message.  
  
     IT Professionals can deploy the WCF Channel for WebSphere applications by using the Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, which provides IIS-like features that were previously only available to HTTP-based applications. The WCF Channel for WebSphere MQ can communicate activation requests that are received over WebSphere MQ. This allows developers to create more dynamic services and better integration of existing messaging with new solutions that are based on WCF.  
  
-   **BizTalk Pipeline Component for Host Data Conversion**  
  
     BizTalk professionals use a broad range of technologies to move information across their enterprise, to connect and integrate heterogeneous application and systems. Popularly, enterprises use the built-in BizTalk adapters for file transfer protocol (FTP) and IBM WebSphere MQ. Although these adapters are capable, they lack built-in record-level data conversion. Most BizTalk developers have created transforms to extract information from binary files and message, or merely to convert character messages one code page to another. By using BizTalk Pipeline Component for Host Data Conversion, you can easily add message or record conversion to existing BizTalk adapters that do not offer built-in transformation or formatting, such as the adapters for WebSphere MQ and File Transfer Protocol (FTP). Host data conversion is based on  existing HIS technologies and offers an intuitive Designer plug-in for Visual Studio with COBOL, RPG, and XSD import/export. The host data conversion runtime engine converts numeric, datetime, and string data types for a range of platforms and locales. This allows BizTalk developers to produce BizTalk message pipeline-level solutions that scale and perform well.  
  
##  <a name="Removed"></a> Removed Features  
 The following features have been removed from Host Integration Server.  
  
-   **Microsoft Data Link Control (DLC) network protocol and the DLC 802.2 Link Service** have been removed from Host Integration Server. You should use the Internet Protocol-Data Link Control (IP-DLC) Link Service that is based on the industry-standard High Performance Routing over Internet Protocol (HPR/IP).  
  
-   **NetView Run Command (NVRunCmd) Service** has been removed from Host Integration Server. You should use File Transfer Protocol (FTP) over TCP/IP as an alternative to the NVRunCmd feature.  
  
-   **Microsoft ODBC Driver for DB2** has been removed from Host Integration Server. You should use the Microsoft ADO.NET Data Provider for DB2, Microsoft OLE DB Provider for DB2, or Microsoft BizTalk Adapter for DB2.  
  
-   **Microsoft Host File Transfer ActiveX Control** has been removed from Host Integration Server. You should use the Microsoft ADO.NET Data Provider for Host Files or Microsoft BizTalk Adapter for Host Files.  
  
-   **Microsoft AS/400 Data Queues ActiveX Control** has been removed from Host Integration Server. The HIS team would like feedback from customers who require direct access to AS/400 data queues to prioritize work on a replacement technology. You can provide feedback about the Host Integration Server on the Microsoft Connect site listed below.  
  
-   **Microsoft Message Queue to MQ Series Bridge (MSMQ Bridge)** has been removed from Host Integration Server. You should use Microsoft BizTalk Server 2010 together with one of the two Microsoft BizTalk Adapters for IBM WebSphere MQ (MQ Series), or the Microsoft WCF Channel for WebSphere MQ.  
  
-   **Transaction Integrator support for Component Object Model (COM) libraries** has been removed from Host Integration Server. You should use the Transaction Integrator Designer to convert COM type libraries to .NET assemblies, and then re-deploy the components.  
  
-   **Transaction Integrator support for .NET Remoting** has been removed from Host Integration Server. You should use the HIS support for direct .NET calls.  
  
## HIS Community  
 Plug into the Host Integration Server community to connect with other IT professionals and get answers to your questions, read the latest from bloggers, see webcasts, learn about events, and participate in the TechNet Wiki.  
  
|Resource|Location|  
|--------------|--------------|  
|Host Integration Server Home|[http://go.microsoft.com/fwlink/?LinkId=187949](http://go.microsoft.com/fwlink/?LinkId=187949)|  
|Host Integration Server Blog|[http://go.microsoft.com/fwlink/?LinkId=142377](http://go.microsoft.com/fwlink/?LinkId=142377)|  
|Host Integration Server Forum|[http://go.microsoft.com/fwlink/?LinkId=191382](http://go.microsoft.com/fwlink/?LinkId=191382)|  
|Host Integration Server on Microsoft Connect|[http://go.microsoft.com/fwlink/?LinkId=187946](http://go.microsoft.com/fwlink/?LinkId=187946)|  
|TechNet Wiki|[http://go.microsoft.com/fwlink/?LinkId=198099](http://go.microsoft.com/fwlink/?LinkId=198099)|  
  
## Contacting Microsoft About Documentation Issues  
 The Host Integration Server documentation team solicits your feedback about the documentation. Are you finding the information that you need quickly? Are there any gaps in content coverage? Please send your comments and suggestions to us by using the feedback link in the online Help or by contacting us through the Host Integration Server on Microsoft Connect link.  
  
## See Also  
 [Overview of HIS 2010](../HIS2010/overview-of-his-2010.md)   
 [Getting Started with HIS 2010](../HIS2010/getting-started-with-his-2010.md)