---
description: "Learn more about: Security between the Oracle Database and the adapter"
title: "Security between the Oracle Database and the adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security between the Oracle Database and the adapter
The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides no support for helping to secure communication between it and the Oracle database. You must provide a security mechanism to help ensure appropriate levels of authorization, authentication, data privacy, and data integrity for data exchanges between the adapter and the Oracle database.

 One possible mechanism for helping to provide more security across the network is Internet Protocol Security (IPsec). IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks. For more information about IPsec and about using IPsec with Microsoft products, see the Microsoft TechNet article "IPsec" at [https://go.microsoft.com/fwlink/?LinkId=196851](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10)).

 However, in the absence of security mechanisms like IPsec, the administrator must configure native Oracle data encryption and integrity to ensure secure data exchanges between the adapter client and the Oracle database. For detailed information about configuring native Oracle data encryption and integrity, see [https://go.microsoft.com/fwlink/p/?LinkId=140032](https://go.microsoft.com/fwlink/p/?LinkId=140032).

 You must supply user name password credentials to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses these credentials to authenticate the user on the Oracle database when it opens a connection. These credentials provide a level of authorization on the Oracle database for the connection.

> [!NOTE]
>  The credentials used by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to establish a connection on the Oracle database do not provide message-level or transport-level authentication or authorization for data traveling across the network. They are only used to open a connection and authenticate the user on the Oracle database.

 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides a number of methods through which you can supply these credentials. For information about how to more securely provide Oracle credentials in BizTalk solutions, see [Security with the Oracle Database adapter and Biztalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md). For information about how to more securely provide Oracle database credentials in programming solutions, see [Secure programming with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md).

## Managing Audit Logs
 Audit logs enable you to store information about the actions performed by various clients on your enterprise software, and helps usage monitoring and problem tracking. However, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not provide any way to manage audit logs for the actions performed by the adapter clients on the Oracle database. This might pose a security threat as the adapter clients can repudiate the actions performed by them on the Oracle database. To mitigate this issue, you must enable audit trail in Oracle to log the actions performed by the adapter clients on the Oracle database.

## See Also
[Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)
[Best Practices](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)