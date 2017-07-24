---
title: "&lt;Host Name&gt; Properties Dialog Box, Properties Tab (FTP Adapter Send Handler) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.ftp.handler.send.props"
helpviewer_keywords: 
  - "FTP adapters, properties"
  - "send handlers, FTP adapters"
  - "properties, FTP adapters"
  - "FTP adapters, send handlers"
ms.assetid: c289993c-3bb8-4755-b4d7-5504c5e10a7c
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Properties Tab (FTP Adapter Send Handler)
Use the **Properties** tab to configure the send handler for the FTP adapter.  
  
|**Use this**|**To do this**|  
|------------------|--------------------|  
|**Maximum Files**|Specify the maximum number of files per BizTalk Server batch.<br /><br /> Valid values: from 1 through 200<br /><br /> Default value: 50|  
|**Address**|Specify the address of the firewall, either a DNS name or an IP address.|  
|**Mode**|Specify the mode in which the adapter connects to the FTP server.<br /><br /> Valid values: Passive and Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> Default value: Active|  
|**Password**|Specify the password for the firewall.|  
|**Port**|Specify the port for the firewall.<br /><br /> Valid values: from 1 through 65535<br /><br /> Default values:21|  
|**Type**|Specify the type of firewall deployed.<br /><br /> Valid values: Socks 4, Socks 5, None<br /><br /> Default value: None|  
|**User**|Specify the user name for the firewall.|  
|**Account**|Optional. Specify the account name for the FTP server.|  
|**After Put**|Specify the FTP command to run after the file PUT. Separate commands with a semicolon (;).|  
|**Allocate Storage**|Specify the use for allocating storage space for some legacy host systems.<br /><br /> Valid values: Yes and No<br /><br /> Default value: No|  
|**Before Put**|Specify the FTP commands to run before the file PUT, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required. **Note:**  QUIT command is not supported before the file PUT.|  
|**Log**|Specify the location to save a copy of a log file. Use this file to diagnose error conditions when you send or receive files through FTP.|  
|**Password**|Specify the user password to log on to the FTP server.|  
|**Representation**|Select how FTP sends the data, either binary or ASCII.<br /><br /> Valid values: binary and ASCII<br /><br /> Default value: binary|  
|**Target File Name**|Specify the pattern for the destination file name.<br /><br /> Default value: %MessageID%.xml|  
|**User Name**|Specify the user name to log on to the FTP server.|  
|**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.|  
|**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> Valid values:  Implicit or Explicit<br /><br /> Default value:  Explicit|  
|**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server.<br /><br /> This property is applicable only if the **Use SSL** property is set to Yes.<br /><br /> Valid values:  Yes or No<br /><br /> Default value:  Yes|  
|**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br /><br /> Valid values:  Yes or No<br /><br /> Default value:  No|  
|**Temporary Folder**|Specify the location for a temporary folder on the FTP server. If a binary file is uploaded, this folder is used to guarantee recovery from a transfer failure.<br /><br /> If an ASCII file is uploaded, the file is first uploaded to this folder and then moved to the destination FTP folder. In the event of transfer failure, the adapter restarts upload. **Note:**  Use of this property supports atomic writing of files.|  
  
## See Also  
 [How to Configure an FTP Send Handler](http://msdn.microsoft.com/library/8d41e23f-0e7d-49b1-8698-30408e91349c)   
 [Enhancements to the FTP Adapter](http://msdn.microsoft.com/library/c5ea3d2d-2d7c-4571-b458-de01d8912e87)