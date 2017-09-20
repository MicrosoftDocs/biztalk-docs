---
title: "Security between Oracle E-Business Suite and the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88f5f8ed-48d5-4420-9fdb-0a6860b95ac4
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security between Oracle E-Business Suite and the adapter
The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides no support for helping to secure communication between it and the Oracle database. You must provide a security mechanism to help ensure appropriate levels of authorization, authentication, data privacy, and data integrity for data exchanges between the adapter and the Oracle database.  
  
 One possible mechanism for helping to provide more security across the network is Internet Protocol Security (IPsec). IPsec is a framework of open standards for protecting communications over Internet Protocol (IP) networks. For more information about IPsec and about using IPsec with Microsoft products, see the Microsoft TechNet article "IPsec" at [http://go.microsoft.com/fwlink/?LinkID=196851](http://go.microsoft.com/fwlink/?LinkID=196851).  
  
 However, in the absence of security mechanisms like IPsec, the administrator must configure native Oracle data encryption and integrity to ensure secure data exchanges between the adapter client and Oracle E-Business Suite.  
  
 You must supply user name password credentials to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses these credentials to authenticate the user on the Oracle database when it opens a connection. These credentials provide a level of authorization on the Oracle database for the connection.  
  
> [!NOTE]
>  The credentials used by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to establish a connection on the Oracle database do not provide message-level or transport-level authentication or authorization for data traveling across the network. They are only used to open a connection and authenticate the user on the Oracle database.  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides a number of methods through which you can supply these credentials. For information about how to more securely provide Oracle credentials in BizTalk solutions, see [Security with the Oracle E-Business Suite adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md). For information about how to more securely provide Oracle database credentials in programming solutions, see [Security Considerations for Adapters](../../core/security-considerations-for-adapters.md).  
  
## Managing Audit Logs  
 Audit logs enable you to store information about the actions performed by various clients on your enterprise software, and helps usage monitoring and problem tracking. However, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] does not provide any way to manage audit logs for the actions performed by the adapter clients in Oracle E-Business Suite. This might pose a security threat as the adapter clients can repudiate the actions performed by them in Oracle E-Business Suite. To mitigate this issue, you must enable audit trail in Oracle to log the actions performed by the adapter clients in Oracle E-Business Suite. For information about how you can set up Oracle audit trails, see the “Oracle Workflow - Oracle E-Business Suite Process” white paper at [http://go.microsoft.com/fwlink/?LinkId=136388](http://go.microsoft.com/fwlink/?LinkId=136388).  
  
## See Also  
 [Secure your Oracle EBS applications](secure-your-oracle-ebs-applications.md)  
 [Best practices to secure the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md)