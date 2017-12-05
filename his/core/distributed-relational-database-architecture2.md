---
title: "Distributed Relational Database Architecture2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09b427d0-b1f2-4cef-9918-71a031f0f2ef
caps.latest.revision: 4
---
# Distributed Relational Database Architecture
Database technology has enabled departments and individual users to save their information locally—as opposed to centrally managed stores owned by the organization's information systems group. Along with local storage and database query tools comes greater flexibility and ease of access to information. As more databases became distributed, a need emerged for users to access data stored remotely. IBM devised the Distributed Relational Database Architecture (DRDA) to enable their customers to access remote, distributed database systems across hardware platforms.  
  
 DRDA supports most dialects of the Structured Query Language (SQL) for access to relational database management systems (RDBMS). SQL is an international standard that defines a standardized language for accessing database management systems (DBMS). DRDA implementations generally support SQL in two ways: static (embedded) SQL, where the SQL commands are embedded directly in the application program or DB2 package and prepared as an extra step in the process of compiling the application or package; and dynamic or interactive (callable) SQL, where the user passes SQL commands as function calls at run time.  
  
 A client that complies with DRDA is referred to as an application requesters (AR) because it requests data from the DRDA server. A servers that complies with DRDA is referred to as an application server (AS). Typically, application servers are implemented as the link or gateway to the RDBMS.  
  
 DRDA supports access to stored procedures on DB2. SQL applications can invoke stored procedures or user-written programs on DB2 using the SQL **CALL** statement. Also, DRDA supports access to static SQL embedded in DB2 packages. SQL applications can invoke static SQL statements using an **EXEC STATIC** syntax on an OLE DB Command.  
  
 The OLE DB Provider for DB2 is an application requester implementation that can initiate DRDA commands to be serviced by a remote target DRDA application server represented by IBM DB2. On the Windows operating system, the Microsoft DRDA application requester can run as a dynamic link library within the OLE DB provider and consumer process. This enables the integration of the DRDA service with other host applications using the IBM DRDA protocols and DRDA servers resident on the host. Microsoft host-based software is not required. IBM offers DB2 DRDA application servers for most popular environments. For more information, see [Host Platforms for DB2](../core/host-platforms-for-db2.md).  
  
## See Also  
 [OLE DB Provider for DB2 Programmer's Guide](../core/ole-db-provider-for-db2-programmer-s-guide.md)