---
title: "connectionManager | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7133786c-389f-46e3-8cdc-97a9ae78188f
caps.latest.revision: 2
ms.author: "dwrede"
---
# connectionManager
The connectionManager element contains the network, security and failover settings for managing in-bound DRDA client connections.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <connectionManager>                        </connectionManager>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The connectionManager type is the Microsoft.HostIntegration.Drda.Server.TcpConnectionManager, which supports in-bound DRDA AR client connections across a TCP/IP network connection.|true|n/a|  
|port|xs:int|The Port attribute defines the TCP/IP Port number on which the DRDA Service must listen for in-bound DRDA Application Requester client connection requests. This optional attribute accepts an integer value. The default value is 446. If you specify a port different from the default DRDA port 446, then DRDA clients must specify the non-default port number in requests to the computer or they will not connect to the DRDA Service.|false|446|  
|useSsl|xs:boolean|The useSSL attribute instructs the DRDA Service to use Secure Sockets Layer (SSL) Version 3.0 and Transport Layer Security (TLS) Version 1.0 when responding to in-bound TCP/IP network connections. This optional attribute accepts a Boolean value. The default value is false.|false|false|  
|sslCertificatePath|xs:string|The sslCertificatePath attribute specifies the SSL or TLS certificate Common Name (CN). This optional attribute is required when useSSL=true, and accepts a string value. The default value is an empty string.|false|n/a|  
|partnerServers|xs:string|The partnerServers attribute defines the list of secondary server computers. This optional attribute is required when isPrimary=false, and accepts a string value. The default value is an empty string. The list is comprised of a TCP/IP address or alias colon-separated by a TCP/IP port number. The TCP/IP address can be defined in either IPv4 or IPv6 format. The list can contain multiple partner server computers semi-colon delimited.|false|n/a|  
|isPrimary|xs:boolean|The isPrimary attribute instructs the DRDA Service whether to operate in a primary role within a group of servers. This optional attribute accepts a Boolean value. The default value is true.|false|true|  
|pingInterval|xs:int|The pingInterval attribute instructs the DRDA Service how frequently to monitor the health of partner server computers, by executing an EXCSAT (Exchange Server Attribute) flow and checking for an EXCSATRD (EXCSAT Reply Data). This optional attribute accepts an integer value. The default value is 10000 milliseconds (10 seconds).|false|10000|  
|performanceCountersOn|xs:boolean|The peformanceCountersOn attribute instructs the DRDA Service to collect information into performance counters. This optional attribute accepts a Boolean value. The default value is false.|false|false|  
|clientIpAddressesAllowed|xs:string|The clientIpAddressesAllowed attribute restricts the DRDA Service to accepting in-bound TCP/IP network connections from a list of known DRDA AR client computers. This optional attribute accepts a string value. The default value is an empty string, which allows the DRDA Service to respond to all in-bound client connection requests. The list is comprised of a TCP/IP address or alias semi-colon delimited. The TCP/IP address can be defined in either IPv4 or IPv6 format.|false|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|