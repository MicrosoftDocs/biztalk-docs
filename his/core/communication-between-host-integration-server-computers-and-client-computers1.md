---
title: "Communication Between Host Integration Server Computers and Client Computers1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cafcb4c8-73bd-4d5c-84ba-7076293eb3a3
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Communication Between Host Integration Server Computers and Client Computers
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses two connections between the systems running SNA Applications and the SNA Gateway.  The first connection is used to communicate information about the HIS subdomain, such as available resources.  This is called the Sponsor connection.  It is established by the component SNABASE.   The second connection is used for the SNA traffic traveling through the SNA Gateway to the host systems.  It is established directly between the SNA application and the SNA Server service on the SNA Gateway.  This is called the Application connection.  Both of these connections use TCP/IP and are secured through NTLM or Kerberos. 
 
**Sponsor connection**
 
Host Integration Server Resource location is accomplished using an out of band connection created by the component SNABASE.  This component runs on both the server and the client, providing a communication channel over which the client can receive information about the subdomain.  The SNABASE service on the HIS servers acts as a sponsor, locating available resources from the entire subdomain on the client's behalf.    The client has two methods for finding a sponsor server; using a list of server names entered into the configuration tool or by querying Active Directory.   When SNABASE starts it will attempt to establish a sponsor connection.  If it is configured to use a list of names, it will retrieve this list from the registry.  If it is configured to use Active Directory it will query the global catalog for service connection points whose service binding information matches the subdomain name.  Once it has retrieved the list of sponsors it will attempt to connect to the first server listed, unless the Random Select option is enabled.   If the first server selected is unavailable, it will continue down the list until it finds an available server.  When an available server is found, the client will be authenticated using Kerberos or NTLM and then be provided with a list of all the servers available in the subdomain.  

Determining which method to use
 
Sponsor server names
* Allows control over which server are used as sponsor servers 
* Allows control over the order of the sponsor server list 
 
Active Directory
* All servers in the subdomain available as sponsors
* Changes in the subdomain are automatically reflected in Active Directory
 
**Application Connection**
 
SNA applications use IBM specific APIs to interact with applications on an IBM Host.  In order for this communication to occur a session must be established with resources on the IBM Host.  Sessions with the host are provided by the SNA Gateway portion of Host Integration Server.   When an SNA application attempts to connect to a resource on an IBM host, a query will be sent on the sponsor connection to determine which SNA Gateway in the subdomain can provide access to that resource.  It will then connect to the SNA Server service on that server and will be authenticated using Kerberos or NTLM.   Once the logon completes an access check will be done to determine if the uses has rights to the resource.  If they do have access to the resource, a connection will be established between the SNA application on Windows and the SNA application on the host system.  
  
 In this Section  
  
 [Host Integration Server Client and SNA Communications](../core/host-integration-server-client-and-sna-communications2.md)  
  
## See Also  
 [SNA Service](../core/sna-service2.md)