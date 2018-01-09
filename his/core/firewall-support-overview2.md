---
title: "Firewall Support Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f1f4d04-eaa1-4746-b324-6401b68f17f1
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Firewall Support Overview
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] client computers and servers can interoperate with screening routers, where the client computer knows the address of the Host Integration Server computer. Host Integration Server client computers and servers can also interoperate with full-blown Internet firewalls, where the end user is not allowed to know the IP address of the Host Integration Server computers.  
  
 A firewall is a network security device that restricts access to network resources by allowing traffic only through specified port numbers. These port numbers are commonly defined in software components to allow Internet firewalls to filter packets based on port number, thereby denying or accepting their propagation to the private network. In many instances, the services of a firewall are provided in conjunction with a network router that bridges two network segments together.  
  
 [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] can be configured to use specific software port numbers, allowing administrators of Internet firewalls to filter packets based on port number. By assigning specific destination port numbers to Host Integration Server components, Host Integration Server can interoperate with screening routers and full-blown firewalls.  
  
 If the Host Integration Server address is known, the client workstation configures the appropriate port and destination IP of the Host Integration Server computer in the client software, for example, 1477 and 128.124.1.2. Alternatively, the Host Integration Server computer's service port numbers can be changed to the port number requested by the client.  
  
 You can configure destination port numbers in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] for end-user and Administrator clients using TCP/IP.  
  
 Each network transport has the following three components for which you can assign destination ports.  
  
 **DatagramPort**  
 This port is used for datagram (mostly broadcast or multicast) traffic. Use the **Server Broadcasts** dialog box in the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA Manager to control which transport is used for server-to-server communication.  
  
 **SnaBasePort**  
 This is the port to which the server SnaBase listens for new client sponsor connections. Sponsor connections are used by the Host Integration Server client to learn about the SNA subdomain in which it participates.  
  
 **SnaServerPort**  
 This is the port where the SNASERVR.EXE waits for new application session requests.  
  
 If the Host Integration Server address is not known, the Host Integration Server IP transport replaces the real destination IP address with the address of a firewall. The firewall then maps the connection request to the actual Host Integration Server computer. This takes place when the transport opens a connection to a Host Integration Server-based computer for application sessions or a sponsor connection.  
  
 Host Integration Server supports firewalls on TCP/IP networks. For more information about configuring a firewall, consult your network documentation.  
  
 It is also possible to create IP mappings which, by overriding service table entries, replace a specified IP address with a firewall address. To create a mapping, add an IPMapping key under the SnaTcp key, and then add a REG_SZ value for each mapping. An example is shown below:  
  
```  
IPMapping  
xxx.xxx.x.xxx = yyy.yy.yy.yyy  
```  
  
 With this mapping, any attempts at establishing a connection with *xxx.xxx.x.xxx* will instead connect to *yyy.yy.yy.yyy*.  
  
 For additional information on firewall support, including client-side registry settings and the use of DLS with firewalls, see the following Knowledge Base articles: Q139508, Q164590, Q224303, and Q215838.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)