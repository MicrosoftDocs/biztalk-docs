---
description: "Learn more about: Connections and the SnaCfg Utility"
title: "Connections and the SnaCfg Utility1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2897a23d-5516-47d6-ad32-adcda1cfe223
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Connections and the SnaCfg Utility
SnaCfg is a useful command-line utility for deploying and managing SNA Server configurations.  
  
 The following table describes the command-line parameters.  
  
|Property|Description|Validation|  
|-|-|-|  
|/conntype:type|Connection type.|IP-DLC.|  
|/RemoteAddress:adr|Address of the remote DLUS service. This property is not accessible through the user interface. It provides a way of establishing a direct connection with DLUS rather than routing the connection through the NNS.|Valid IP address or DNS name.|  
|/PrimNetworkName:name|Network name of the primary DLUS server.|1–8 characters, SNA Type A string.|  
|/PrimCPName:name|Control point name of the primary DLUS server.|1–8 characters, SNA Type A string.|  
|/BackupNetworkName:name|Network name of the backup DLUS server.|1–8 characters, SNA Type A string.|  
|/BackupCPName:name|Control point name of the backup DLUS server.|1–8 characters, SNA Type A string.|  
|/DLURRetryType:N|DLUR retry type.|0 indicates none<br /><br /> 1 indicates infinite<br /><br /> 2 indicates limited|  
|/DLURRetryLimit:N|DLUR retry limit. This parameter is invalid unless the DLUR retry type is set to limited.|1–65534|  
|/DLURRetryDelay:N|Delay after a DLUR retry. This parameter is invalid unless the DLUR retry type is set to limited.|1–65535|  
|/RetryLimit:N|Number of the connection retries.|0 indicates unlimited<br /><br /> 1–65534 number of retries|  
|/RetryDelay:N|Delay after a connection retry.|0–327670, must be a factor of 5.|  
|/XIDFormat:N|XID type.|Set to:<br /><br /> 1 – "Format 3"|  
|/RemoteNetName:name|This value is always set to the network name of the IP-DLC link service.|Must be left blank for a new connection.|  
|/RemoteCPName:name|This value is always set to the control point name of the IP-DLC link service.|Must be left blank for a new connection.|  
  
## See Also  
 [Creating an IP-DLC Connection](../core/creating-an-ip-dlc-connection1.md)   
 [Viewing Connections](../core/viewing-connections1.md)   
 [Defining Dependent LUs](../core/defining-dependent-lus1.md)   
 [Secure Deployment of the IP-DLC Link Service](../core/secure-deployment-of-the-ip-dlc-link-service2.md)
