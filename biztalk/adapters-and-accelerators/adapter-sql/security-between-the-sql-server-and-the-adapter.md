---
description: "Learn more about: Security between the SQL Server and the adapter"
title: "Security between the SQL Server and the adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security between the SQL Server and the adapter
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is compatible with the standard methods, such as SSO and IPSEC used to secure data exchanges with the database server. Unsecured data exchanges can expose data to unauthorized actors. For information about security issues with SQL Server, see [Security Considerations for SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation) in the SQL documentation.

 You can improve the security of data exchanges by using Internet Protocol Security (IPsec). IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks. With IPSec, any data exchanged between the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and the SQL server over the network is encrypted, making it difficult for unauthorized actors to use the data. For more information about IPsec and about using IPsec with Microsoft products, see the Microsoft TechNet article [IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10)).

 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports SSO and Integrated Security for authentication on the connections that it establishes with the database. With SSO, the credentials are encrypted and stored in the registry. The system uses these credentials to determine access instead of requiring the user to enter them where they might be seen by unauthorized actors. Integrated Security uses the credentials of the logged on user to access the SQL server. This also eliminates the need for users to enter credentials. The database administrator must configure SQL to accept the users credentials for Integrated Security to work correctly.

## See Also
[Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)