---
title: "Security and Protection3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23574afe-4086-46df-8e02-2ee069970e29
caps.latest.revision: 9
---
# Security and Protection
The information contained in the following sections details securing your [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] environment, including Enterprise Single Sign-On.  
  
 For information about Single Sign-On, see [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md).  
  
 **SQL Server**  
  
 When you are accessing a SQL Server database:  
  
-   Because the Resync service will access this database -- and the database may service multiple, unsecured domains -- you should always use a local SQL Server database and never grant remote access to it.  
  
-   Use only Windows integrated security, and restrict access to only privileged Windows accounts.  
  
-   Use only [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] security groups which were created with the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Configuration Wizard.  
  
 **General Considerations**  
  
 In addition to the general guidelines elsewhere in this section, the following specific recommendations can help you increase the security of your hisHostIntServNoVersion deployment. Since all of these actions are performed during deployment or configuration, procedures are located in the appropriate sections of this documentation.Whereas these recommendations apply across the entire product, the [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation1.md) section also offers information specifically for TI users.  
  
 When you are connecting via SNA Protocol:  
  
-   When connecting to an upstream Host Integration Server computer, use client/server encryption.  
  
-   When implementing SNA Open Gateway Architecture (SOGA) Distributed Link Service (DLS) across wide area networks, use server-to-server encryption.  
  
-   Locate upstream Host Integration Server computers within the data center using secure Token Ring, Ethernet, Bus and Tag Channel, or ESCON fiber channel attachments.  
  
 When you are connecting via TCP/IP protocol:  
  
-   Use upstream Windows software router computers or hardware routers to encrypt the TCP/IP traffic.  
  
-   Locate the upstream router within the data center using either secure Token Ring or Ethernet connections to the host.  
  
-   Because DRDA AR sometimes stores data in plain text:  
  
    -   Use direct network connections over a private segment, with static IP or SNA addresses.  
  
    -   Use IPsec where supported for IP communications between host and Windows servers.  
  
-   When connecting an SNA LU6.2 network to a mainframe or AS/400, with the Host Integration Server computer deployed as the SNA gateway to a downstream Host Integration Server computer, use Host Integration Server server-to-server data encryption.  
  
-   For SNA LU6.2 network connections to mainframe, use the IP-DLC Link Service in conjunction with IPsec.  
  
-   Use encryption that is part of the Host Integration Server server-to-server and client-to-server connections.  
  
-   When connecting to a mainframe DB2 for z/OS, use IPsec on an IP-DLC, and also use NNS on the target system to utilize direct connections to DLUS and APPN Peer resources.  
  
 When you are accessing DB2 DUW over the IP Resync Service:  
  
-   Increase the level of security access rights to the SQL Server database which stores the UOWID mapping tables.  
  
-   Use the (default) separate SQL Server database, as opposed to one shared with other applications.  
  
 To protect unencrypted data and credentials in the com.cfg file:  
  
-   Implement IPsec.  
  
-   Deploy the Host Integration Server computer in an isolated network segment.  
  
-   Increase security settings on the host account used for session security.  
  
 When using the TN3270 Server:  
  
-   Stop and restart the TN3270 Server whenever a new CRL is downloaded. Otherwise, you will be using an out of date CRL, which could permit unwanted access to the host.  
  
 **Server-to-Host Security**  
  
 The following actions will increase server-to-host security, especially on an APPN Network or UDP sockets for HPR/IP Protocol Traffic:  
  
-   Deploy [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] in a secure network segment, and use encryption that is part of the Host Integration Server server-to-server and client-to-server connections.  
  
-   Use IPsec on the IP-DLC connection.  
  
-   Use NNS on the target system to utilize direct connections to DLUS and APPN Peer resources.  
  
-   Use a direct IP-DLC Connection to CS/390 (DLUS) and NNS, or a direct IP-DLC Connection to a peer APPN node.  
  
 **Additional Security Recommendations**  
  
 Finally, as in the following recommendations, be vigilant about access to every file, connection, or other product component:  
  
-   In general, use System or User DSNs rather than file DSNs, as System and User DSNs are more secure.  
  
-   When using the OLE DB Provider for AS/400 and VSAM, store your HCD files in a secure local folder or share that can only be accessed by the developer and the runtime application.  
  
-   When using Transaction Integrator, place any objects going to CICS or IMS in a remote environment that requires Enterprise Single Sign-On.  
  
-   Be vigilant about your access control list (ACL). Although it is possible to install Host Integration Server and inherit a previous ACL, you should remove any existing ACLs and replace them with new ones.  
  
-   Store Printer Definition Tables (PDTs) and Printer Definition Files (PDFs) in a secure location to prevent their being replaced with a rogue file.  
  
-   Since trace files may contain non-encrypted data, always store them in a secure location, and delete them as soon as trace analysis is complete.  
  
-   Minimize unwanted access to the Resync Service by running it on the same computer as the application it services.  
  
-   Enable LUA Security for TN3270 access to the host, and then add the service account to the Configured Users folder. Among other things, this provides encryption if the TN3270 service uses LUs on another server.  
  
-   Enable LUA Security for TN5250 access to the host. This increases security by requiring explicit assignment of LUs to user records.  
  
-   When using the printing feature associated with the TN3270 Server, reconfigure the display and printer to use the same port. This is necessary because, since these two items are configured separately, they are often inadvertently configured to different ports, and subsequently different security settings.  
  
-   Always use IPsec when using the TN3270 or TN5250 Servers. Although data might be safe between the client and server without IPsec, that same data may become vulnerable between the server and the host. Using IPsec reduces the attack surface, ensures data encryption, and makes access available only to authorized users.  
  
## In This Section  
 [Network Integration (Security)](../core/network-integration-security-1.md)  
  
 [Data Integration (Security)](../core/data-integration-security-1.md)  
  
 [Application Integration (Security)](../core/application-integration-security-1.md)