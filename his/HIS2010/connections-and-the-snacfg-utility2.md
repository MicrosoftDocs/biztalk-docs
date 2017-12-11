---
title: "Connections and the SnaCfg Utility2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 258d4c26-1948-40db-8c83-3e7cb94601e1
caps.latest.revision: 3
---
# Connections and the SnaCfg Utility
SnaCfg is a useful command-line utility for deploying and managing SNA Server configurations.  
  
 The following table describes the command-line parameters.  
  
||||  
|-|-|-|  
|**Property**|**Description**|**Validation**|  
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
 [Creating an IP-DLC Connection](../HIS2010/creating-an-ip-dlc-connection2.md)   
 [Viewing Connections](../HIS2010/viewing-connections2.md)   
 [Defining Dependent LUs](../HIS2010/defining-dependent-lus2.md)   
 [Secure Deployment of the IP-DLC Link Service](../HIS2010/secure-deployment-of-the-ip-dlc-link-service1.md)