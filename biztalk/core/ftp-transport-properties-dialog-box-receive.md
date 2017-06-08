---
title: "FTP Transport Properties Dialog Box, Receive | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.ftp.transport.props1"
helpviewer_keywords: 
  - "FTP adapters, properties"
  - "properties, FTP adapters"
  - "receive locations, FTP adapters"
  - "FTP adapters, receive locations"
ms.assetid: c1eb4f71-3fe9-4c49-9a42-6d7a9858f244
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FTP Transport Properties Dialog Box, Receive
Use the **FTP Transport Properties** dialog box to configure the receive location for the FTP adapter.  
  
> [!NOTE]
>  You can resize the description pane at the bottom of the dialog box by dragging the double-headed arrow that appears on the top border of the pane.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Maximum Files**|Specify the maximum number of files per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> Default value: 0|  
|**Maximum Size**|Specify the maximum number of bytes per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> Default value: 0|  
|**Address**|Specify the address of the firewall, either a DNS name or an IP address.|  
|**Mode**|Specify the mode in which the adapter connects to the FTP server.<br /><br /> Valid values: Passive and Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> Default value: Active|  
|**Password**|Specify the password for the firewall.|  
|**Port**|Specify the port for the firewall.<br /><br /> Valid values: From 1 through 65,535<br /><br /> Default value: 21|  
|**Type**|Specify the type of firewall deployed.<br /><br /> Valid values: None, Socks 4, and Socks 5<br /><br /> Default value: None|  
|**User**|Specify the user name for the firewall.|  
|**Account**|Specify the account name for the FTP server.<br /><br /> This property is optional.|  
|**After Get**|Specify the FTP commands to run after the file GET. Separate commands with a semi-colon (;).|  
|**Before Get**|Specify the FTP commands to run before the file GET. Separate commands with a semi-colon (;). **Note:**  QUIT command is not supported before the file GET.|  
|**Error Threshold**|Specify the number of errors that BizTalk Server can encounter before the location is disabled.<br /><br /> Default value: 10|  
|**File Mask**|Specify the file mask filter to use when transmitting files.|  
|**Folder**|Specify the polling location on the FTP server.|  
|**Log**|Specify the location to save a copy of a log file. You use this file to diagnose error conditions when you send or receive files through FTP.|  
|**Max File Size**|Specify the maximum downloadable file size, in megabytes.<br /><br /> Zero (0) indicates no limit on the file size.<br /><br /> Default value: 100|  
|**Password**|Specify the user password to log on to the FTP server.|  
|**Port**|Specify the port address for this FTP server.<br /><br /> Default value: 21|  
|**Representation**|Select how FTP receives the data.<br /><br /> Valid values: binary or ASCII<br /><br /> Default value: binary|  
|**Server**|Specify the server name or IP address of the FTP server.|  
|**SSO Affiliate**|Specify the Single Sign-On affiliate application.|  
|**Use name list (NLST)**|Specify how the adapter lists files. To view file names instead of the system-defined file listing, set this value to Yes.<br /><br /> Default value: No|  
|**User Name**|Specify the user name to log on to the FTP server.|  
|**Delete After Download**|Specify whether the adapter deletes a file from the FTP server after downloading it.<br /><br /> Default value: Yes<br /><br /> If the adapter does not have permissions to delete a file from the FTP server, set the **Enable Timestamp Comparison** property.|  
|**Enable Timestamp Comparison**|Specify whether the adapter downloads a file again based on its modified timestamp. Set this value to Yes when the adapter does not have sufficient permissions to delete a file from the FTP server.<br /><br /> Default value: No<br /><br /> Set this value to Yes only if the FTP server supports the command MDTM. If the FTP server does not support MDTM, set the **Redownload Interval** property.|  
|**Interval**|Specify the interval number for polling this location. To continuously poll, set this value to zero (0).<br /><br /> Default value: 60|  
|**Redownload Interval**|Specify the interval at the lapse of which the adapter downloads files again. This property is useful when the FTP server does not allow for comparison of the file’s modified timestamp.<br /><br /> Default value: -1<br /><br /> -1 indicates that the adapter will not download the file again.<br /><br /> 0 indicates that the adapter will download the file in each polling cycle.|  
|**Unit**|Specify the type of units for the Interval and Redownload Interval properties.<br /><br /> Valid values: Seconds, Minutes, Hours, and Days<br /><br /> Default value: Seconds|  
|**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.|  
|**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> **Valid values:** Implicit or Explicit<br /><br /> **Default value:** Explicit|  
|**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plaintext.<br /><br /> This property is applicable only if the **Use SSL** property is set to Yes.<br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** Yes|  
|**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** No|  
|**Receive Data Timeout**|Specify the time in milliseconds before the receive call will abort. You use this to prevent a slow server from causing the receive location to stop responding.<br /><br /> **Default value:** 90000|  
|**Temporary Folder**|Specify the location for a temporary folder. You use this location to guarantee recovery from a transfer failure.|  
  
## See Also  
 [How to Configure an FTP Receive Location](../Topic/How%20to%20Configure%20an%20FTP%20Receive%20Location.md)