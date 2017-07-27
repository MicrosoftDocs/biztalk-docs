---
title: "&lt;Host Name&gt; Properties Dialog Box, Properties Tab (FTP Adapter Receive Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.ftp.handler.receive.props"
helpviewer_keywords: 
  - "receive handlers, FTP adapters"
  - "FTP adapters, properties"
  - "properties, FTP adapters"
  - "FTP adapters, receive handlers"
ms.assetid: ebcad2b8-ae85-47d2-97de-a92bde4013a0
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Properties Tab (FTP Adapter Receive Handler)
Use the **Properties** tab to configure the receive handler for the FTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Maximum Files**|Specify the maximum number of files per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> **Default value:** 0|  
|**Maximum Size**|Specify the maximum number of bytes per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> **Default value:** 0|  
|**Address**|Specify the address of the firewall, either DNS name or IP address.|  
|**Mode**|Specify the mode in which the adapter connects to the FTP server.<br /><br /> **Valid values:** Passive or Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> **Default Value:** Active|  
|**Password**|Specify the password for the firewall.|  
|**Port**|Specify the port for the firewall.<br /><br /> **Valid values:** 1 through 65535 inclusive<br /><br /> **Default value:** 21|  
|**Type**|Specify the type of firewall deployed.<br /><br /> **Valid values:** Socks 4, Socks 5, None<br /><br /> **Default value:** None|  
|**User**|Specify the user name for the firewall.|  
|**Account**|Specify the account name for the FTP server.|  
|**After Get**|Specify the FTP commands to run after the file GET. Separate commands with a semicolon (;).|  
|**Before Get**|Specify the FTP commands to run before the file GET. Separate commands with a semicolon (;). **Note:**  QUIT command is not supported before the file GET.|  
|**Error Threshold**|Specify the number of errors that BizTalk Server can encounter before the location is disabled.<br /><br /> **Default value:** 10|  
|**Log**|Specify the location to save a copy of the log file. Use this file to diagnose error conditions when sending or receiving files through FTP.|  
|**Max File Size**|Specify the maximum downloadable file size, in megabytes (MB).<br /><br /> Zero (0) indicates no limit.<br /><br /> **Default Value:** 100|  
|**Password**|Specify the user password to log on to the FTP server.|  
|**Representation**|Select how FTP receives the data.<br /><br /> **Valid Values:** binary or ASCII<br /><br /> **Default Value:** binary|  
|**User Name**|Specify the user name to log on to the FTP server.|  
|**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.|  
|**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> **Valid Values:** Implicit or Explicit<br /><br /> **Default Value:** Explicit|  
|**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plain text.<br /><br /> This property is applicable only if the **Use SSL** property is set to Yes.<br /><br /> **Valid Values:** Yes or No<br /><br /> **Default Value:** Yes|  
|**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br /><br /> **Valid Values:** Yes or No<br /><br /> **Default Value:** No|  
|**Temporary Folder**|Specify the location for a temporary folder. Use this property to guarantee recovery from a transfer failure.|  
  
## See Also  
 [How to Configure an FTP Receive Handler](http://msdn.microsoft.com/library/e9efdf13-3757-4a8b-9b0a-c3ed10ba352e)