---
description: "Learn more about: FTP Adapter Property Schema and Properties"
title: "FTP Adapter Property Schema and Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FTP Adapter Property Schema and Properties
The following table contains the properties in the FTP adapter property schema.  
  
 **Namespace:** `http://schemas.microsoft.com/BizTalk/2003/ftp-properties`
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**RepresentationType**|xs:string|Specifies how the FTP adapter sends data.<br /><br /> **Valid values:** binary or ASCII|  
|**SSOAffiliateApplication**|xs:string|Specifies the Enterprise Single Sign-On affiliate application to use on the FTP send port.|  
|**UserName**|xs:string|Specifies the user name to log on to the FTP server when sending messages.|  
|**Password**|xs:string|Specifies the password to use when logging on to the FTP server when sending messages.|  
|**FirewallPassword**|xs:string|Specifies the password to use on the firewall before logging on to the FTP server.| 
|**BeforePut**|xs:string|Specifies the FTP commands to run before the file PUT, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required.|  
|**AfterPut**|xs:string|Specifies the FTP commands to run after the file PUT. Separate commands with a semicolon (;).|  
|**ReceivedFileName**|xs:string|Specifies the full name of the file from which the FTP adapter reads the message.|  
|**MaxConnections**|xs:unsignedInt|Specifies the maximum number of concurrent FTP connections that can be opened to the server. A value of 0 means no limit.|  
|**CommandLogFileName**|xs:string|Specifies the location to save a copy of a log file that can be used to diagnose error conditions when sending or receiving files through FTP.|  
|**AllocateStorage**|xs:boolean|This option is deprecated in BizTalk Server and use of this property is discouraged.|  
|**PassiveMode**|xs:boolean|Specifies the mode in which the adapter connects to the FTP server.<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> If **PassiveMode** is false then the adapter connects to the FTP server using Active mode. The default value for this property is false.|  
|**SpoolingFolder**|xs:string|Specifies the location for a temporary folder on the FTP server. You use this to ensure recovery from a transfer failure.|  
|**AppendIfExists**|xs:boolean|Decide if you want to append the content when the file already exists on the FTP Server.|
|**UseSsl**|xs:boolean|Specifies whether the FTP adapter must use SSL to communicate with the FTPS server.|  
|**UseDataProtection**|xs:boolean|Specifies whether SSL encryption is used for file transfers. Choose true if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Choose false for the adapter to send and receive data files as plaintext.|  
|**FtpsConnectionMode**|xs:string|Specifies the mode of SSL connection made to the FTPS server.<br /><br /> **Valid Values:** Implicit or Explicit|  
|**ClientCertificateHash**|xs:string|Specifies the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.<br /><br /> Based on this hash, the client certificate is picked up from the personal store of the user account under which the BizTalk host instance is running.|  
|**FtpServerType**|xs:string||
|**ExpandMacros**|xs:boolean||
  
## See Also  
 [Configuring the FTP Adapter](../core/configuring-the-ftp-adapter.md)
 
 [Best practices and recommendations for the FTP Adapter](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)
 
 [FTP Adapter](../core/ftp-adapter.md)
