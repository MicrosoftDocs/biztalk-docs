---
title: "Encrypt the BRE DB connection | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63edd2bb-97f1-4b8b-8cdc-f4792909ca86
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Encrypt the Connection to the BRE Database
Based on the security policy of your company, consider encrypting:  
  
- The credentials transmitted during the logon process.  
  
- The data transmitted across a network between the client computer where the Business Rule Engine (BRE) policy runs and the Rule Engine database.  
  
  This topic describes how to encrypt the connections to BRE databases hosted on SQL Server.  
  
## Encrypt the Connection to the BRE Database
 By default, credentials that are transmitted during the logon process when a client application connects to SQL Server are encrypted. If no certificate has been provisioned on the server, when it starts up, SQL Server generates a self-signed certificate that is used to encrypt logon packets.  
  
 To enable encryption of data that is transmitted across a network between SQL Server and the client for an instance of SQL Server, you should set the **Force Encryption** option on the server to **Yes** or set the **Force Protocol Encryption** option to **Yes** on the client.  
  
 When the **Force Encryption** option is set to **Yes** on the server side, SQL Server uses SSL to encrypt all the communication *between all the clients and the database server*. In other words, all the incoming connections to the server are encrypted. To enable this option on the server, it is recommended that you install a certificate on the server by using SQL Server Configuration Manager. If a certificate is not installed on the server, the server auto-generates a self-signed certificate when the instance is started.  
  
 This self-signed certificate can be used instead of a certificate from a trusted certificate authority, but it does not provide any protection against spoofing identity threats. You should not rely on SSL using self-signed certificates in a production environment or on servers that are connected to the Internet. When the option is set, any client that cannot support encryption is denied access. SQL Server must be restarted after setting the **Force Encryption** option. You can set this option by using the SQL Server Configuration Manager (SQL Server Network Configuration).  
  
 When the **Force Protocol Encryption** is set on the client side, SQL Server uses SSL to encrypt all the communication *between that client and all the servers*. In other words, all the outgoing connections from the client are encrypted. To enable this option on the client side, you should install a certificate on the server if the **Trust Server Certificate** option on the client is set to **No**. If the **Trust Server Certificate** option on the client is set to **Yes**, the client does not validate the server certificate, thereby enabling the use of a self-signed certificate. You can set this option by using the SQL Server Configuration Manager (SQL Native Client Configuration).  
  
 SQL Server also allows you to enable the encryption for a *specific connection from a client to the server* by setting the **Encrypt/Use Encryption for Data** flag to **Yes** in the connection string. However, the BRE automatically generates the connection strings without setting the encryption option to **Yes**. Hence, you cannot encrypt a specific connection to the Rule Engine database server from the client computer. Instead, you should set the **Force Protocol Encryption** option on the client as mentioned in the previous paragraph.