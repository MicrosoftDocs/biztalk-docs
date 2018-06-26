---
title: "Programmatically create the File receive location or send port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 558a414c-60bc-4f62-9397-a023ed4937fb
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Programmatically create the File receive location or send port
How to create a File receive port and send port programmatically. To use the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], go to [Configure the File adapter](../core/configure-the-file-adapter.md).

The File adapter stores its configuration information in the SSO database. You can configure the receive locations and send ports programmatically using the BizTalk Explorer object model. 
 
## Create the receive location

The BizTalk Explorer object model exposes the **IReceiveLocation** configuration interface that contains the **TransportTypeData** read/write property. This property accepts the File receive location configuration property bag in the form of a name/value pair XML string.  
  
The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set. If it is not set, default values for the File receive location configuration are used.  
  
 The following table lists the configuration properties that you can set programmatically for the File receive location.  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|**FileNetFailRetryCount**|Long|The number of attempts to access the receive location on the network share if it is temporarily unavailable.|Integer<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|If not specified, the default value is set to 5 times.|  
|**FileNetFailRetryInterval**|Long|The retry interval in minutes between attempts to access the receive location on the network share if it is temporarily unavailable.|Integer<br /><br /> Minimumvalue: 0<br /><br /> Maximum value: MAX_LONG|If not specified, the default value is set to 5 minutes.|  
|**BatchSize**|Long|The number of files this receive location can submit to the server at one time.|Integer<br /><br /> Minimum value: 1<br /><br /> Maximum value: 256|If not specified, the default value is set to 20 files.|  
|**FileMask**|String|The file mask used by the receive location.|String<br /><br /> The length of the FilePath and FileMask combined cannot exceed 256 characters.|If not specified, the default value is set to *.xml.|  
|**FilePath**|String|The path of the folder monitored by the receive location.|String<br /><br /> Required<br /><br /> The length of the FilePath and FileMask combined cannot exceed 256 characters.|Must be specified **Important:**  The file folder created for the receive location must have write permission for the receive handler credentials configured on the receive location.|  
|**Username**|String|User name for account used to access folder.|Min length: 0<br /><br /> Max length: 256|If neither username or password are specified, host credentials are used.<br /><br /> If null (vt=”1”) then the value stored in configuration database is used.|  
|**Password**|String|Password for account used to access folder.|Min length: 0<br /><br /> Max length: 256|If neither username or password are specified, host credentials are used.<br /><br /> If null (vt=”1”) then the value stored in configuration database is used.|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
   <FilePath vt="8">C:\Temp</FilePath>  
   <BatchSize vt="19">20</BatchSize>  
   <FileMask vt="8">*.xml</FileMask>  
   <FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
   <FileNetFailRetryInterval vt="19">5</FileNetFailRetryInterval>  
   <Username vt=”8”>MyDomain\MyUsername</Username>  
   <Password vt=”8”>PASSWORD</Password>  
</CustomProps>  
  
```  

## Create the send port

Configuration information is stored in a custom XML property bag. The `bts_file_properties.xsd` File send handler property schema defines the File adapter-specific properties. You use these properties to configure the File send ports, as well as for passing adapter-specific information within the server.  
  
The BizTalk Explorer object model exposes the **ITransportInfo** adapter configuration interface for File send ports, which contains the **TransportTypeData** read/write property. This property accepts the File send handler configuration property bag as a name/value pair XML string.  
  
 Setting the **TransportTypeData** property of the **ITransportInfo** interface is not required. If it is not set, the default values for the File send handler configuration are used.  
  
 The following table lists the configuration properties you can set programmatically in the BizTalk Explorer object model for the File send handler location.  
  
|Property name|Type|Description|  
|-------------------|----------|-----------------|  
|**CopyMode**|Long|Define the copy mode to use when writing a message to a file. Valid values are:<br /><br /> **Append (0).** The File send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the File send handler creates a new file.<br /><br /> **Create new (1).** If the file does not exist, the File send handler creates a new file and writes to it. If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the File send handler.<br /><br /> **Overwrite (2).** The File send handler opens a file if it exists and overwrites its content. If the file does not exist, the File send handler creates a new file.|  
|**AllowCacheOnWrite**|Boolean|Defines whether the File adapter uses file system caching when writing messages to a file.<br /><br /> Valid values are:<br /><br /> **True (-1)** The File adapter uses file system caching when writing the output file.<br /><br /> **False (0)** The File send handler does not use file system caching when writing the output file.|  
|**Use temporary file while writing**|Boolean|Defines whether to write the output file to a temporary file first and then rename the file once the write operation has completed. If this option is enabled then the temporary file will be created with the extension **BTS-WIP**.<br /><br /> Valid values are:<br /><br /> **True (-1)** The File adapter creates a temporary file when writing to the target folder.<br /><br /> **False (0)** The File adapter does not create a temporary file when writing to the target folder. **Note:**  This option is only available when the **CopyMode** property is set to a value of **Create new (1)**.|  
  
 If any of the configuration properties do not have a value on the message context, the File send handler uses its default value.  
  
 You can set configuration properties programmatically on a message context. You can set these properties in an orchestration or in a custom pipeline component. The following rules apply when using these properties:  
  
- If the configuration property is set in an orchestration or in a custom pipeline component in a receive pipeline, then:  
  
  -   If a message is sent to a static send port, the property value will be overwritten with the value configured for that send port.  
  
  -   If a message is sent to a dynamic send port, the property value will not be overwritten.  
  
- If a configuration property is set in a custom pipeline component in a send pipeline, then:  
  
  -   The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port.  
  
  The following code shows the format of the XML string you can use to set the properties:  
  
```  
<CustomProps>  
   <CopyMode vt="19">0</CopyMode>  
   <AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
   <UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
</CustomProps>  
```  


