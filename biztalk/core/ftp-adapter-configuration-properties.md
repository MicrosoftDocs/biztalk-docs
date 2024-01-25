---
description: "Learn more about: FTP Adapter Configuration Properties"
title: "FTP Adapter Configuration Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FTP Adapter Configuration Properties
The following table lists the configuration properties that you can set for an FTP adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Specify the full path of the location monitored by the receive location.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|serverAddress|VT_BSTR|Specify the server name or IP address of the FTP server.|None|None|  
|serverPort|VT_BSTR|Specify the TCP port over which to communicate with the target FTP server.|None|None|  
|userName|VT_BSTR|Specify the user name that is used to access the FTP server.|None|None|  
|password|VT_BSTR|Specify the password that is used to access the FTP server.|This value is always masked when exporting a binding file. This property must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
|fileMask|VT_BSTR|Specify the file mask filter to use when transmitting files.|None|None|  
|targetFolder|VT_BSTR|Specify the polling location on the FTP server.|None|None|  
|commandLogFilename|VT_BSTR|Specify the location to save a copy of the log file.|None|You use this file to diagnose error conditions when sending or receiving files through the FTP adapter.|  
|representationType|VT_BSTR|Select how FTP adapter receives the data.|Valid values are:<br /><br /> -   Binary<br />-   ASCII|The default value is Binary.|  
|spoolingFolder|VT_BSTR|Specify the location for a temporary folder on the FTP server. You use this to guarantee recovery from a transfer failure.|None|None|  
|receiveDataTimeOut|VT_BSTR|Specify the time in milliseconds before the receive call will abort. This is used to prevent a slow server from causing the receive location to hang.|None|The default value is 90000.|  
|maximumBatchSize|VT_BSTR|Specify the maximum number of bytes per BizTalk Server batch.|None|None|  
|maximumNumberOfFiles|VT_BSTR|Specify the maximum number of files per BizTalk Server batch.|None|None|  
|passiveMode|VT_BSTR|Specify the mode in which the adapter connects to the FTP server.|Valid values are:<br /><br /> -   Passive<br />-   Active|The default value is Active.|  
|useNLST|VT_BSTR|Specify this as Yes to retrieve only file names instead of the default system-defined file listing.|Valid values are:<br /><br /> -   Yes<br />-   No|The default value is No.|  
|beforeGet|VT_BSTR|Specify the FTP commands to execute before the file GET.|Separate commands with a semicolon (;) **Note:**  QUIT command is not supported before the file GET.|None|  
|afterGet|VT_BSTR|Specify the FTP commands to execute after the file GET.|Separate commands with a semicolon (;)|None|  
|firewallType|VT_BSTR|Specify the type of firewall deployed.|Valid values are:<br /><br /> -   None<br />-   Socks 4<br />-   Socks 5|The default value is None.|  
|firewallAddress|VT_BSTR|Specify the address of the firewall (DNS name or IP address).|None|None|  
|firewallPort|VT_BSTR|Specify the port for the firewall.|Valid values are from 1 to 65535.|The default value is 21.|  
|firewallUserName|VT_BSTR|Specify the user name for the firewall.|None|None|  
|firewallPassword|VT_BSTR|Specify the password for the firewall.|None|None|  
|pollingUnitOfMeasure|VT_BSTR|Specify the type of units for the pollingInterval property.|Valid values are:<br /><br /> -   Seconds<br />-   Minutes<br />-   Hours<br />-   Days|The default value is Seconds.|  
|pollingInterval|VT_BSTR|Specify the interval value for polling this location.|None|To continuously poll, set this value to 0.<br /><br /> The default value is 60.|  
|redownloadInterval|VT_BSTR|Specify the interval in seconds after which FTP adapter will download the file again.|This property is applicable only if both deleteAfterDownload and enableTimeComparison properties are set to No.|A value of -1 indicates that the adapter will not download the file  again.<br /><br /> The default value is -1.|  
|ssoAffiliateApplication|VT_BSTR|Specify the Single-Sign-On (SSO) affiliate application.|None|None|  
|errorThreshold|VT_BSTR|Specify the number of errors that BizTalk Server can encounter before the location is disabled.|None|The default value is 10.|  
|maxFileSize|VT_BSTR|Specify the maximum downloadable file size, in megabytes.|None|A value of 0 indicates no limit on the file size.<br /><br /> The default value is 100.|  
|useSsl|VT_BSTR|Specify this as Yes if the FTP adapter must use SSL when communicating with the FTPS server.|Valid values are:<br /><br /> -   Yes<br />-   No|The default value is No.|  
|useDataProtection|VT_BSTR|Specify this as Yes if the FTP adapter must use SSL encryption when sending and receiving files to and from the FTPS server.|This property is valid if the useSsl property is set to Yes.<br /><br /> Valid values are:<br /><br /> -   Yes<br />-   No|The default value is Yes.|  
|ftpsConnMode|VT_BSTR|Specify the mode of SSL connection made to the FTPS server.|Valid values are:<br /><br /> -   Explicit<br />-   Implicit|The default value is Explicit.|  
|clientCertificateHash|VT_BSTR|Specify  the SHA1 hash of the client certificate that must be used in the SSL negotiation.|None|Based on this hash, the client certificate is picked up from the personal store of the user account under which the BizTalk host instance is running.|  
|deleteAfterDownload|VT_BSTR|Specify this as Yes if the adapter must  delete the  file from the FTP server after the  download is complete.|Valid values are:<br /><br /> -   Yes<br />-   No|The default value is Yes.|  
|enableTimeComparison|VT_BSTR|Specify this as Yes if the adapter must download a file again when there is a change in the file’s timestamp.|This property is valid only when deleteAfterDownload is set to No.<br /><br /> The target FTP server must support MDTM command for this feature.<br /><br /> Valid values are:<br /><br /> -   Yes<br />-   No|The default value is No.|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>ftp://localhost:21/in/*.xml</uri><serverAddress>localhost</serverAddress><serverPort>21</serverPort><userName>domain\testuser</userName><password>******</password><fileMask>*.xml</fileMask><targetFolder>in</targetFolder><commandLogFilename>c:\temp\realftplog.txt</commandLogFilename><representationType>binary</representationType><maximumBatchSize>0</maximumBatchSize><maximumNumberOfFiles>0</maximumNumberOfFiles><passiveMode>False</passiveMode><firewallType>NoFirewall</firewallType><firewallPort>21</firewallPort><pollingUnitOfMeasure>Seconds</pollingUnitOfMeasure><pollingInterval>5</pollingInterval><errorThreshold>10</errorThreshold><maxFileSize>5000</maxFileSize><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><deleteAfterDownload>True</deleteAfterDownload><enableTimeComparison>False</enableTimeComparison></Config></AdapterConfig></CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for an FTP adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Specify the full path of the location to send data to.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|serverAddress|VT_BSTR|Specify the address of the firewall, either a DNS name or an IP address.|None|None|  
|serverPort|VT_BSTR|Specify the port address for the FTP server.|None|The default value is 21.|  
|userName|VT_BSTR|Specify the user name to log on to the FTP server.|None|None|  
|password|VT_BSTR|Specify the password to log on to the FTP server.|This value is always masked when exporting a binding file. This property must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
|accountName|VT_BSTR|Specify the account name for the FTP server.|Optional|None|  
|targetFolder|VT_BSTR|Specify the location to move the files to on the FTP server.|None|None|  
|targetFileName|VT_BSTR|Specify an alternative name for the file. Retaining the default name will guarantee unique message names for each message sent.|None|The default value is %MessageID%.xml.|  
|commandLogFilename|VT_BSTR|Specify the location to save a copy of the log file. Use the log file to diagnose error conditions when sending or receiving files through FTP server.|None|None|  
|representationType|VT_BSTR|Select how FTP sends the data, either as binary or as ASCII.|Valid values are:<br /><br /> -   binary<br />-   ASCII|The default value is binary.|  
|beforePut|VT_BSTR|Specify the FTP commands to run before the file PUT, such as commands to change default values on the FTP server.|Separate commands with a semicolon (;). **Note:**  QUIT command is not supported before the file PUT.|No open command is required.|  
|afterPut|VT_BSTR|Specify the FTP commands to run after the file PUT.|Separate commands with a semicolon (;).|None|  
|allocateStorage|VT_BSTR|Specify whether to allocate storage space for legacy host systems.|Valid values are:<br /><br /> -   Yes<br />-   No|The default value is No.|  
|spoolingFolder|VT_BSTR|Specify the location for a temporary folder on the FTP server. You use this to guarantee recovery from a transfer failure if the transfer mode is binary. If the transfer mode is ASCII, the adapter restarts the upload.|None|None|  
|connectionLimit|VT_BSTR|Specify the maximum number of concurrent FTP connections that can be opened to the server.|None|A value of 0 means no limit.|  
|passiveMode|VT_BSTR|Specify whether to use passive mode or active mode.|Valid values are:<br /><br /> -   True (passive mode)<br />-   False (active mode)|The default value is False (active mode).|  
|firewallType|VT_BSTR|Select the type of firewall deployed.|Valid values are:<br /><br /> -   Socks 4<br />-   Socks 5<br />-   None|The default value is None.|  
|firewallAddress|VT_BSTR|Specify the address of the firewall, either a DNS name or an IP address.|None|None|  
|firewallPort|VT_BSTR|Specify the port for the firewall.|Valid values are from 1 to 65535.|The default value is 21.|  
|firewallUserName|VT_BSTR|Specify the user name for the firewall.|None|None|  
|firewallPassword|VT_BSTR|Specify the password for the firewall.|This value is always masked when exporting a binding file. This property must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
|ssoAffiliateApplication|VT_BSTR|Specify the Single-Sign-On (SSO) affiliate application.|None|None|  
|useSsl|VT_BSTR|Specify this as Yes if the FTP adapter must use SSL when communicating with the FTPS server.|Valid values are:<br /><br /> -   Yes<br />-   No|The default value is No.|  
|useDataProtection|VT_BSTR|Specify this as Yes if the FTP adapter must use SSL encryption when sending and receiving files to and from the FTPS server.|This property is valid if useSsL is set to Yes.<br /><br /> Valid values are:<br /><br /> -   Yes<br />-   No|The default value is Yes.|  
|ftpsConnMode|VT_BSTR|Specify the mode of SSL connection made to the FTPS server.|Valid values are:<br /><br /> -   Explicit<br />-   Implicit|The default value is Explicit.|  
|clientCertificateHash|VT_BSTR|Specify the SHA1 hash of the client certificate that must be used in the SSL negotiation.|None|Based on this hash, the client certificate is picked up from the personal store of the user account under which the BizTalk host instance is running.|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><serverAddress>TestServer</serverAddress><serverPort>21</serverPort><userName>testuser</userName><password>******</password><accountName>testuser</accountName><targetFolder>output</targetFolder><targetFileName>%MessageID%.xml</targetFileName><commandLogFilename>c:\logfile\ftpsendlog.txt</commandLogFilename><representationType>binary</representationType><beforePut>CDW dir</beforePut><afterPut>CDUP </afterPut><allocateStorage>False</allocateStorage><spoolingFolder>tempfolder</spoolingFolder><connectionLimit>0</connectionLimit><passiveMode>False</passiveMode><firewallType>Socks4</firewallType><firewallAddress>TestServer</firewallAddress><firewallPort>21</firewallPort><firewallUserName>domain\testuser</firewallUserName><firewallPassword>******</firewallPassword><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><uri>ftp://TestServer:21/output/%MessageID%.xml</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  When specifying TransportTypeData configuration data for an adapter built using the Adapter Framework, all the name/value pairs that are used must be stored into the \<AdapterConfig\> element. Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type then the \< \> characters in the data must be escaped.
