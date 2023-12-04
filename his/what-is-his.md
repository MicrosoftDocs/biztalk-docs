---
title: What is HIS
description: Learn how Host Integration Server (HIS) enables enterprise organizations to integrate existing IBM host systems, programs, messages and data with on-premises and Azure Cloud applications. 
ms.prod: host-integration-server
ms.topic: overview
ms.date: 11/24/2023
---

# What is HIS

Microsoft Host Integration Server (HIS) technologies and tools enable enterprise organizations to integrate existing IBM host systems, programs, messages and data with on-premises and Azure Cloud applications. HIS allows IT administrators to securely and efficiently connect new systems to existing systems using industry-standard High Performance Routing (HPR) and Transmission Control Protocol (TCP) over Internet Protocol (IP). This reduces operating expenses and total cost of ownership while supporting existing and new computing workloads.

Host Integration Server empowers enterprise developers to deliver new applications more quickly and with less custom coding. Developers who use Visual Studio can be more productive than those who use IBM host development tools and technologies because they do not require knowledge of host systems and infrastructure. HIS empowers knowledge workers and decision-makers to analyze and report vital information faster. They can access data in host data sources using tools such as Power BI. This eliminates the need to schedule host developers to write programs to extract and convert host structures.

Host Integration Server also supports enterprises who are conducting legacy modernization by providing technologies for hybrid connectivity and applications coexistence. Enterprises who decide to migrate workloads from their Mainframes or Midranges to the Azure Cloud, can use the Azure Logic Apps connectors to support their transition to Azure Cloud.
  
 The following sections provide an overview of the five HIS technology areas:
  
- Network Integration
  
- Data Integration
  
- Application Integration
  
- Message Integration
  
- Security Integration
  
<a name="Network"></a>

## Network Integration  

Network integration services connect Azure applications and infrastructure to existing IBM mainframe and midrange Systems Network Architecture (SNA). SNA Services operate as a gateway function, supporting logical unit types (LU0, LU1, LU2, LU3, and LU6.2), connecting across an SNA Advanced Peer to Peer Network (APPN), as a Low Entry Network (LEN) node, or as a Branch Network node using High Performance Routing over Internet Protocol (HPR/IP). Administrators can deploy SNA applications on Windows computers using the HIS client that connects to the HIS server via TCP/IP, supporting required SNA device types.

HIS Network Integration services connect workstations, devices and virtual machines to existing host systems, while reducing network infrastructure complexity and costs. The Network Integration services can be used in hybrid environments (Azure to host systems on-premises, host systems on-premises to Azure or Modernized workloads in Azure to other Azure workloads).

Host Print Service provides server-based 3270 and 5250 printer emulation, allowing host applications to connect to Windows Server  printers, enabling centralized control and sharing of resources. Resynchronization Services support standard Synchronization Level 2 (Sync Level 2), also known as the Two-Phase Commit (2PC) protocol, for distributed transactions over IP-DLC (HPR/IP) and TCP/IP. TN3270 Service, with Secure Sockets Layer (SSL) and Transport-Layer Security (TLS), allows deployment of simple terminal and printer emulation programs, while offloading the host system from supporting non-native TCP/IP-to-SNA protocol conversion. 
  
To modernize host programs in terminal or batch processing systems, HIS offers Session Integrator and Systems Network Architecture (SNA) Software Development Kit libraries. The SDK allows enterprise developers to create custom applications, run samples, and use tutorials to learn more about Host Integration Server. For more information, see [Network Integration Programmer's Guide](core/network-integration-programmer-s-guide2.md).  

<a name="Data"></a>

## Data Integration

Host Integration Server data integration components offer enterprise IT professionals and developers direct access to vital information stored in IBM DB2 database management systems and record-oriented host file systems. HIS includes multiple data clients and one data service. The data clients connect to remote IBM DB2 databases, IBM Informix databases, and IBM host file systems. The data server connects remote IBM clients to Microsoft SQL Server. The data clients support a set of data providers (ADO.NET, OLE DB, and ODBC), data adapters (BizTalk), and tools (HIS Data Access Tool and Visual Studio Data Designers).  
  
The HIS Data Access Tool with Data Source Wizard guides the knowledge worker, IT professional or enterprise developer to define and manage connections to DB2, Informix and host file systems. Visual Studio  tools, such as Server Explorer and DataSet Designer, assist the enterprise developer to generate code for Azure  applications.  

HIS Data Integration solutions and technologies enable direct data access to DB2, Informix and host file systems, plus remote DB2 client access to Microsoft SQL Server.  
  
SQL Server tools, including Management Studio and Business Intelligence Development Studio, help IT professionals and enterprise developers to deliver data warehouse solutions based on information stored in DB2 databases, Informix databases, and host file systems, for on-line transaction processing and decision-support. Power BI helps IT professionals to integrate DB2 and host files system data to provide coherent, visually immersive, and interactive insights. 
  
The Microsoft Service for DRDA (Distributed Relational Database Architecture) is an Application Server (AS) that enables DRDA Application Requester (AR) clients, such as IBM DB2 for z/OS and DB2 for i5/OS, to execute static SQL statements mapped to SQL Server stored procedures. The DRDA Service provides host-initiated data integration essential to enterprises during a phased workload migration, or for daily operations in support of remote batch or business intelligence solutions.  
  
For more information, see [Data Integration (Planning)](core/data-integration-planning-1.md).  

<a name="application"></a>

## Application Integration

Transaction Integrator (TI) allows enterprise developers to call business rules in host mainframe (Customer Information Control System and Information Management System) and midrange (IBM System i) programs using Visual Studio and the .NET Framework. TI is comprised of a Visual Studio plug-in designer, administration tool (TI Configuration Tool) and runtime components that integrate host applications with the .NET Framework. Enterprise developers can define .NET clients using an intuitive COBOL or RPG source code import wizard within the TI designer. 
  
HIS Transaction Integrator allows enterprise developers to integrate and extend host transaction programs.  
  
Transaction Integrator for host-initiated processing allows a computer running Microsoft server software to function as a peer to IBM mainframe and midrange host systems, enabling host developers to access and update Microsoft server applications using familiar host programming models and communications infrastructure. BizTalk Adapter for Host Applications is based on TI technology, allowing enterprises to connect BizTalk Server solutions to existing mainframe (CICS and IMS) or midrange (IBM System i) server programs. For more information, see [Application Integration (Planning)](core/application-integration-planning-2.md).  

<a name="message"></a>

## Message Integration

Message integration technologies allow enterprise IT professionals and developers to integrate IBM MQ with Microsoft server infrastructure. WCF Channel for IBM MQ allows enterprise developers to send/receive MQ messages between WCF and heterogeneous programs, such as mainframe CICS and IMS, or homogenous applications, such as a peer WCF channel stack. Built on technology from TI, Message Integrator offers a Visual Studio plug-in designer to define metadata for converting the MQ message payload and a .NET interface for wrapping instances of the WCF Channel across the IBM MQ infrastructure.  
  
HIS Message Integrator enables IT professionals and enterprise developers to integrate BizTalk Server and Windows Communications Foundation applications with existing programs, messages and data through IBM MQ infrastructure.  
  
BizTalk Adapter for MQ uses the IBM MQ to communicate with remote  MQ Queue Managers, without needing to deploy and manage IBM MQ Server for Windows, to efficiently exchange messages with line-of-business applications across the enterprise. To convert MQ data messages, HIS offers a BizTalk Pipeline Component for Host Data Conversion, which is based on TI designer and TI data conversion technologies. Starting with HIS 2016 a Microsoft Client for MQ is included to allow Windows .NET developers access IBM WebSphere MQ Servers directly.  The HIS 2020 MQSC Adapter for BizTalk can be configured to use either the IBM MQ Client for the Microsoft Client for MQ for the underlying communications.

<a name="Security"></a>

## Security Integration

Enterprise Single Sign-On (ESSO) allows enterprises to integrate Windows Active Directory (AD) accounts to IBM host system credentials. Enterprise IT administrators map host credentials to AD accounts, storing these in an encrypted SQL Server database. Enterprise IT professionals and developers can retrieve these mappings at runtime from within HIS features and using the ESSO SDK.  
  
IT administrators define one or more ESSO “affiliate applications”, which are logical names to a group of mapping. Each affiliate application has multiple user mappings, for example, users in Active Directory are mapped to their corresponding RACF credentials. Enterprise developers and administrators refer to these ESSO affiliate applications, when defining connections using HIS technologies, making it easy to configure and use single sign-on.  
  
IT administrators can configure multiple levels of auditing, to track access to the mapping database, as well as to provide an extra layer of accounting information on end user and application access to the backend host system and applications. For more information, see [Enterprise Single Sign-On](esso/enterprise-single-sign-on1.md).  
  
## See Also

[HIS 2016 - What's New, Release Notes, System Requirements, and Installation](install-and-config-guides/his-2016-what-s-new-release-notes-system-requirements-and-installation.md)
[HIS 2013 - What's New, Install, and Configure](install-and-config-guides/his-2013-what-s-new-install-and-configure.md)
