---
title: "Goals of the OLE DB Provider for AS-400 and VSAM | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 363abb8e-e16a-41d4-af85-f950a963074b
caps.latest.revision: 6
---
# Goals of the OLE DB Provider for AS-400 and VSAM
For the majority of enterprises today, much mission-critical information resides on IBM mainframe z/OS and midrange i5/OS computers. This information is stored in records on the z/OS and i5/OS file systems. This information is created, owned, and often accessible by only host-based applications. In the mainframe environment, these applications include Customer Information Control System (CICS), Information Management System (IMS) and DB2 relational database management system; other commercial applications; and a large number of custom applications written in COBOL, PL/I, and other languages. In the i5/OS environment, these applications include primarily DB2 and commercial applications, plus a large number of custom report program generator (RPG); COBOL/400 and control language (CL) applications. Not all of these data sources are SQL-accessible. Many of the host data stores contain non-SQL-accessible data that is owned by something other than a traditional relational database management system (RDBMS).  
  
 These same enterprises rely on vast networks of personal computers to enable their users to achieve business goals. End users invariably rely on network e-mail, Windows productivity applications such as Office, personal database programs such as Access and group database programs such as SQL Server Analysis Services, to accomplish their daily tasks. It is essential for these same users to incorporate data stored on host systems into their regular correspondence, analysis, and reports.  
  
 Common methods of accessing host data, including the bulk file transfer protocol (FTP) do not provide the detailed, record-level access required for cost-effective, more secure, and meaningful integration of host and personal computer systems. In many cases, end users employ antiquated means of data integration. These methods include copying and pasting data from a terminal emulation screen, retyping information from host application reports, and importing text files containing comma-delimited values that use host EBCDIC-to-computer ASCII file transfer. These methods are not efficient although widely used and are not supported by products from independent software vendors (ISVs).  
  
 The challenge is how to provide direct record-level access to this valuable data without going through the host application. Much of the renewed interest in improved access to host data sources is a result of the growth in the use of Web technology as a mechanism for delivering information and enabling information workers with direct data access for analysis and reporting. Fast and inexpensive methods of record-level access are needed to deliver modern, three-tiered information systems during this era of cost-cutting and budget tightening. Additional uses of this direct data access are specific queries and Web-based reporting.  
  
 It is common for corporate management to rethink host data storage and the appropriate software used to provide data access. For enterprise IT organizations, the answer to these issues is in rewriting the arguably outdated host-based business rules with server-based, or even client-based, business logic.  
  
 The goal of the OLE DB Provider for AS/400 and VSAM is to provide customers and solution providers with the means to integrate desktop applications with this wealth of data residing on host computers, without having to make changes to the backend application tier.