---
title: "FTP Transport Properties Dialog Box, Send | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.ftp.transport.props2"
helpviewer_keywords: 
  - "FTP adapters, properties"
  - "properties, FTP adapters"
  - "FTP adapters, send ports"
  - "send ports, FTP adapters"
ms.assetid: 0cdcb574-2574-4d56-be60-8c7d2e14e425
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FTP Transport Properties Dialog Box, Send
Use the **FTP Transport Properties** dialog box to configure the send port for the FTP adapter.  
  
> [!NOTE]
>  You can resize the description pane at the bottom of the dialog box by dragging the double-headed arrow that appears on the top border of the pane.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address**|Specify the address of the firewall, either a DNS name or an IP address.|  
|**Mode**|Specify the mode in which the adapter connects to the FTP server.<br /><br /> **Valid values:** Passive and Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> **Default value:** Active|  
|**Password**|Specify the password for the firewall.|  
|**Port**|Specify the port for the firewall.<br /><br /> **Valid values:** From 1 through 65,535<br /><br /> **Default value:** 21|  
|**Type**|Specify the type of firewall deployed.<br /><br /> **Valid values:** None, Socks 4, and Socks 5<br /><br /> **Default value:** None|  
|**User**|Specify the user name for the firewall.|  
|**Account**|Optional. Specify the account name for the FTP server. This option is deprecated in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and use of this property is discouraged.|  
|**After Put**|Specify the FTP commands to run after the file **PUT**. Separate commands with a semi-colon (;).|  
|**Allocate Storage**|Specify whether to allocate storage space for legacy host systems. This option is provided for backward compatibility but is not used by [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].<br /><br /> **Valid values:** No, and Yes<br /><br /> **Default value:** No|  
|**Before Put**|Specify the FTP commands to run before the file **PUT**, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required. **Note:**  QUIT command is not supported before the file PUT.|  
|**Folder**|Specify the location to move the files to on the FTP server.|  
|**Log**|Specify the location to save a copy of a log file. Use this file to diagnose error conditions when you send or receive files through FTP.|  
|**Password**|Specify the user password to log on to the FTP server.|  
|**Port**|Specify the port address for this FTP server.<br /><br /> **Default value:** 21|  
|**Representation**|Select how FTP sends the data, either binary or ASCII.<br /><br /> **Valid values:** binary or ASCII<br /><br /> **Default value:** binary|  
|**Server**|Specify the server name or IP address of the FTP server.|  
|**SSO Affiliate**|Specify the Single Sign-On affiliate application.|  
|**Target File Name**|Specify an alternative name for the file. Retaining the default name will guarantee unique message names for each message sent.<br /><br /> **Default value:** %MessageID%.xml|  
|**User Name**|Specify the user name to log on to the FTP server.|  
|**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.|  
|**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> **Valid values:** Implicit or Explicit<br /><br /> **Default value:** Explicit|  
|**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plain text.<br /><br /> This property is applicable only if the **Use SSL** property is set to Yes.<br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** Yes|  
|**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** No|  
|**Connection Limit**|Specify the maximum number of concurrent FTP connections that can be opened to the server. A value of 0 means no limit.<br /><br /> **Default value:** 0 **Note:**  This property replaces the registry entry that was used in earlier versions of BizTalk Server to govern the connection limit. The registry entry used to control the Connection Limit is ignored by [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].|  
|**Temporary Folder**|Specify the location for a temporary folder on the FTP server. If a binary file is uploaded, this folder is used to guarantee recovery from a transfer failure.<br /><br /> If an ASCII file is uploaded, the file is first uploaded here and then moved to the destination FTP folder. In the event of transfer failure, the adapter restarts the upload.<br /><br /> Use of this property supports atomic writing of files.|  
  
## See Also  
 [Restrictions on Using Macros in File Names](http://msdn.microsoft.com/library/ac60829d-b076-4630-aea5-a59b32d6250f)   
 [How to Configure an FTP Send Port](http://msdn.microsoft.com/library/03e45656-2f29-4410-a2ee-a830f958cb55)   
 [Enhancements to the FTP Adapter](http://msdn.microsoft.com/library/c5ea3d2d-2d7c-4571-b458-de01d8912e87)