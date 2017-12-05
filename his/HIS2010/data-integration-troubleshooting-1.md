---
title: "Data Integration (Troubleshooting)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8895a76-2f31-4c46-8c7a-c6fad99db925
caps.latest.revision: 11
---
# Data Integration (Troubleshooting)
The data providers for DB2 return two types of errors in the form of SQLSTATE and SQLCODE formatted error strings, which administrators and developers can use to troubleshoot issues. The data providers return DB2 server error strings in the form of standard SQLSTATE with SQLCODE as part of the OLE DB IErrorInfo and MsDb2Exception interfaces. You can research the description of the DB2 server error, based on the SQLSTATE and SQLCODE, in the IBM DB2 Messages and Codes reference for the applicable DB2 platform and version. The data providers for DB2 and host files return DDM RLIO and DRDA protocol error strings in the form of standard SQLSTATE HY000 and 08S01with SQLCODE as part of the OLE DB IErrorInfo and interfaces. Administrators and developers can research the description of the DDM DRDA protocol error, based on the SQLCODE error string, in the Distributed Relational Database Architecture (DRDA) protocol documentation. This is published as an industry standard through [Open Group](http://www.opengroup.org/). You can download DRDA V5 Vol. 1: Distributed Relational Database Architecture, publication number C112 and V5 Vol. 3: Distributed Data Management Architecture, publication number C114, published July 2011, from [http://www.opengroup.org/standards/ea](http://www.opengroup.org/standards/ea). Administrators and developers can research the description of the DDM RLIO protocol error, based on the SQLODE error string, in the Distributed Data Management reference for i5/OS and IBM DFSMS DFM Guide and Reference for z/OS.  
  
## In This Section  
 [Error Types by Feature](../HIS2010/error-types-by-feature.md)  
  
 [Distributed Data Management (DDM) Protocol Errors](../HIS2010/distributed-data-management-ddm-protocol-errors.md)  
  
 [Distributed Relational Database Architecture (DRDA) Protocol Errors](../HIS2010/distributed-relational-database-architecture-drda-protocol-errors2.md)  
  
 [Record-Level Input/Output (RLIO) Protocol Errors](../HIS2010/record-level-input-output-rlio-protocol-errors2.md)  
  
 [SNA Network Errors](../HIS2010/sna-network-errors.md)  
  
 [TCPIP Network Client Errors](../HIS2010/tcpip-network-client-errors2.md)  
  
 [Sign-On Errors](../HIS2010/sign-on-errors1.md)  
  
 [DB2OLEDB Transaction Errors](../HIS2010/db2oledb-transaction-errors.md)  
  
 [SQL Server Integration Services (Troubleshooting)](../HIS2010/sql-server-integration-services-troubleshooting-2.md)  
  
 [SQL Server Replication (Troubleshooting)](../HIS2010/sql-server-replication-troubleshooting-2.md)  
  
 [SQL Server Analysis Services (Troubleshooting)](../HIS2010/sql-server-analysis-services-troubleshooting-1.md)  
  
 [Static SQL for DB2 (Troubleshooting)](../HIS2010/static-sql-for-db2-troubleshooting.md)  
  
 [Visual Studio Data Design Tools](../HIS2010/visual-studio-data-design-tools.md)  
  
 [Code Page Conversion Errors](../HIS2010/code-page-conversion-errors.md)  
  
 [Capturing Problems through Tracing](../HIS2010/capturing-problems-through-tracing.md)  
  
 Add DB2 Database Errors  
  
## Reference  
  
## Related Sections  
  
## See Also  
 [Troubleshooting](../HIS2010/troubleshooting1.md)