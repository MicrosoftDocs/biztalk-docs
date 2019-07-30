---
title: "Link Service and the LnkCfg Utility1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc11196a-5cdd-4b94-baa1-03181e46a1f3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Link Service and the LnkCfg Utility
LnkCfg is a useful command-line utility for deploying and managing link services. The format of the command line for configuring the link service is specified as follows.  
  
 LINKCFG LINKSVC "Title"  
  
 /SERVER:servername  
  
 /LSTYPE:"IP-DLC Link Service"  
  
 /PRIMARYNNS:NNSServer  
  
 [/BACKUPNNS:NNSServer]  
  
 [/LOCALADDRESS:ipaddress] or [/ADAPTER:adaptername]  
  
 /NETWORKNAME:networkname  
  
 /CPNAME:name  
  
 [/UseDynamicPuDefinition:value]  
  
 /NODEID:"xxx.xxxxx"  
  
 /LENNODE:lennode  
  
 /USERID:user  
  
 /PASSWORD:password  
  
 [/RECEIVEACK:number]  
  
 [/LIVETIME:number]  
  
 [/CMDMAXRETRY:number]  
  
 [/MAXACTIVATION:number]  
  
 [/ACTIVATIONDELAY:number]  
  
 [/MAXBTUSEND:number]  
  
 [/MAXBTURCV:number]  
  
 [/NOPREFERREDNNS:value]  
  
 [/VRNNAMES:VRN1;VRN2;  
  
 [/USEIPV6:value]  
  
 [/VRNnotLimitedResource:value]  
  
 [/DisableProgressiveARB:value]  
  
 [/DelayedPathSwitchTimer:value]  
  
 The following table describes the command-line parameters.  
  
||||  
|-|-|-|  
|**Property**|**Description**|**Content**|  
|"Title"|Title of the link service.|1-128 characters.|  
|/SERVER:servername|Name of the server.|Valid server name.|  
|/PRIMARYNNS:NNSServer|Primary network node server.|DNS name or IP address.|  
|/BACKUPNNS:NNSServer|Backup network node server.|DNS name or IP address.|  
|/ADAPTER:adaptername|Name of the local adapter. /ADAPTER and /LOCALADDRESS arguments should not be used together.|Name of the physical or logical adapter on the computer.|  
|/LOCALADDRESS:ipaddress|Local address. /ADAPTER and /LOCALADDRESS arguments should not be used together.|Valid IP address or server name.|  
|/NETWORKNAME:networkname|Network name of the Branch Network Node implemented by the link service.|1-8 characters SNA Type A string.|  
|/CPNAME:name|Control point name of the Branch Network Node implemented by the link service.|1-8 characters SNA Type A string.|  
|/NODEID:"xxx.xxxxx"|Identity of the Branch Network Node implemented by the link service.|String in format HHH.HHHHH where H is a hexadecimal digit.|  
|/LENNODE:lennode|Name of the SNA Server service which will be associated with this link service node.|Name of SNA Server service on the local computer.|  
|/UseDynamicPuDefinition:value|Use dynamically defined PU definitions on the host|YES&#124;NO|  
|/USERID:user|User account the service will run under|string|  
|/PASSWORD:password|Password for the user account|string|  
|[/RECEIVEACK:number]|Receive ACK timeout for HPR protocol|Number of milliseconds|  
|[/LIVETIME:number]|Livetime timeout of HPR protocol|Number of milliseconds|  
|[/CMDMAXRETRY:number]|Indicates the number of times to retransmit a data frame|Number of times to retry|  
|[/MAXACTIVATION:number]|Indicates the number of time the link service will attempt to activate the connection|Number of times to try activation|  
|[/ACTIVATIONDELAY:number]|Indicates the delay in seconds between retries|Delay in seconds|  
|[/MAXBTUSEND:number]|Maximum BTU size in bytes for sent packages|Size in bytes|  
|[/MAXBTURCV:number]|Maximum BTU size in bytes for receive packages|Size in bytes|  
|[/NOPREFERREDNNS:value]|When checked the link service will use the first available NNS.  When enabled, it will switch back to the Primary NNS whenever it is available|YES&#124;NO|  
|[/USEIPV6:value]|Indicates the link service should use IPv6 protocol to communicate with the host|YES&#124;NO|  
|[/VRNNAMES:VRN1;VRN2;|Specifies a virtual routing node to join|Name of the VRN|  
|[/VRNnotLimitedResource:value]|This indicates to links using a VRN are not limited resources|YES&#124;NO|  
|[/DisableProgressiveARB:value]|Forces the link service to only negotiate responsive mode ARB.|YES&#124;NO|  
|[/DelayedPathSwitchTimer:value]|Indicates the delay before a path switch is initiated|Number of seconds|  
  
## See Also  
 [Managing IP-DLC Link Services](../core/managing-ip-dlc-link-services2.md)