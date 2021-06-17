---
description: "Learn more about: Configuring DRDA AR Client Connections"
title: "Configuring DRDA AR Client Connections | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9025c59-5f41-45d5-937a-a1151b01a0f9
caps.latest.revision: 7
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring DRDA AR Client Connections
The DRDA Service handles communication with DRDA AR clients across TCP/IP network connections. The DRDA Service supports optional encryption and failover features to improve security and reliability. You can edit the MsDrdaService.exe.config file to instruct the DRDA Service on how to manage the DRDA AR client connections. The **connectionManager** element of the MsDrdaService.exe.config file contains the network, security and failover settings for managing in-bound DRDA client connections. The **connectionManager** type is the Microsoft.HostIntegration.Drda.Server.TcpConnectionManager, which supports in-bound DRDA AR client connections across a TCP/IP network connection.  
  
### Network  
 The DRDA Service listens and responds to in-bound TCP/IP network connections on a specified network port.  
  
#### TCP/IP Listener Port  
 The **port** attribute defines the TCP/IP Port number on which the DRDA Service must listen for in-bound DRDA Application Requester client connection requests. This **optional** attribute accepts an **integer** value. The default value is **446**. If you specify a port different from the default DRDA port 446, then DRDA clients must specify the non-default port number in requests to the computer or they will not connect to the DRDA Service.  
  
#### Transaction Log Synchronization IP Address  
 The **resyncIpAddress** attribute instructs the DRDA Service the TCP/IP address to send to the DRDA Client in the DRDA Access Relational Database Reply Message (ACCRDBRM), following a successful data connection to the target SQL Server database. The DRDA Client uses the **resyncIpAddress** value and the configured **port** value to establish a transaction log synchronization connection. This optional attribute accepts a **string** value. The default value is an **empty string**, which instructs the DRDA Service to return the TCP/IP address used by the DRDA Client on the data connection.  
  
#### Transaction Log Synchronization Port  
 The DRDA Service listens for in-bound DRDA Client transaction log synchronization connections on the same TCP/IP Listener Port used for in-bound DRDA Client data connections. See TCP/IP Listener Port for more information.  
  
### Security  
 The DRDA Service supports Secure Sockets Layer 3.0 (SSL) and Transport Layer Security 1.0 (TLS) to encrypt the authentication and data between DRDA AR client and DRDA Service.  
  
#### Client IP Addresses Allowed  
 The **clientIpAddressesAllowed** attribute restricts the DRDA Service to accepting in-bound TCP/IP network connections from a list of known DRDA AR client computers. This **optional** attribute accepts a **string** value. The default value is an **empty string**, which allows the DRDA Service to respond to all in-bound client connection requests. The list is comprised of a TCP/IP address or alias semi-colon delimited. The TCP/IP address can be defined in either IPv4 or IPv6 format. For example, 123.34.45.57; 123.34.45.58 defines a valid client list in IPv4 network address format.  
  
#### Secure Sockets Layer and Transport Layer Security  
 The **useSSL** attribute instructs the DRDA Service to use Secure Sockets Layer (SSL) Version 3.0 and Transport Layer Security (TLS) Version 1.0 when responding to in-bound TCP/IP network connections. This **optional** attribute accepts a **Boolean** value. The default value is **false**.  
  
 The **sslCertificatePath** attribute specifies the SSL or TLS certificate contained in an X.509 certificate file, including file path, file name, and file extension. This **optional** attribute is required when useSSL=true, and accepts a **string** value. The default value is an **empty string**. For example, “c:\testdir\testssl.cer” is a fully-qualified file path and file name with file extension containing information for a X.509 certificate. For more information on certificates, see [https://technet.microsoft.com/library/cc754122.aspx](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754122(v=ws.11)).  
  
### Failover  
 The DRDA Service can operate within a group to provide fault tolerant failover. The group is defined by specifying a local service role (primary or secondary), available failover partner servers, and a ping interval for monitoring the health of servers within a group.  
  
#### Primary Server  
 The **isPrimary** attribute instructs the DRDA Service whether to operate in a primary role within a group of servers. This **optional** attribute accepts a **Boolean** value. The default value is **true**. The primary server will respond to all DRDA AR client requests by processing EXCSAT (Exchange Server Attributes), ACCSEC (Access Security) and ACCRDB (Access Relational Database), including returning a SRVLST (Server List) on the ACCRDBRM (ACCRDB Reply Message). The Server List contains a weighted priority list of primary (highest weighted value) and secondary servers (lowest weighted values), to inform the DRDA AR clients to which DRDA Service computer to connect.  
  
#### Partner Servers  
 The **partnerServers** attribute defines the list of secondary server computers. This **optional** attribute is required when isPrimary=false, and accepts a **string** value. The default value is an **empty string**. The list is comprised of a TCP/IP address or alias colon-separated by a TCP/IP port number. The TCP/IP address can be defined in either IPv4 or IPv6 format. The list can contain multiple partner server computers semi-colon delimited. For example, 123.34.45.57:446; 123.34.45.58:446 defines a valid partner server list in IPv4 network address format.  
  
#### Ping Interval  
 The **pingInterval** attribute instructs the DRDA Service how frequently to monitor the health of partner server computers, by executing an EXCSAT (Exchange Server Attribute) flow and checking for an EXCSATRD (EXCSAT Reply Data). This optional attribute accepts an **integer** value. The default value is **10000** milliseconds (10 seconds).  
  
#### Performance Monitors Counters  
 The **peformanceCountersOn** attribute instructs the DRDA Service to collect information into performance counters. This **optional** attribute accepts a **Boolean** value. The default value is **false**. For more information, see section on Performance. See the Performance topic in the Operations book for more information.