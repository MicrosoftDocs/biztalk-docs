---
title: "Infrastructure Management Commands | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2f1a88c-19fc-4384-b6bb-f95962a32921
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Infrastructure Management Commands
The BAM Management (BM) utility configuration commands allow you get and update the BAM configuration.  
  
-   get-config: Gets the BAM configuration file.  
  
-   update-config: Updates the BAM configuration.  
  
-   get-changes: Lists changes to the BAM infrastructure.  
  
-   get-defxml: Gets a file containing all the artifacts in the BAM Primary Import database.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-config Command  
 **Usage**  
  
 **bm.exe get-config -FileName:\<output file> [ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|FileName:\<output file>|The path and name to which to save the configuration file.|  
|Server:\<server>|Optional: The name of the server from which to get the configuration. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database from which to get the configuration. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Retrieves the BAM configuration XML and saves it in the specified file. The **get-config** command will not overwrite the existing file.  
  
 **Examples**  
  
```  
bm.exe get-config -FileName:MyConfig.xml  
bm.exe get-config -FileName:BAMConfiguration.xml -Server:OrdersServer  
```  
  
## update-config Command  
 **Usage**  
  
 **bm.exe update-config -FileName:\<config file>**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|FileName:\<config file>|The path and name of the configuration file from which to update the BAM infrastructure.|  
  
 Updates the configuration on the local computer from a file containing BAM configuration XML. You can add server and database names that do not already exist in the current configuration. Changing server or database names that already have dynamic infrastructure deployed in will fail and bm.exe will report an error.  
  
 If you modify the file drop location for alerts delivered by file. You must restart the SQL Notifications Services. If the NS service is not restarted, alerts will continue being delivered to the original file drop location.  
  
 The file drop location is changed by modifying the following line of the BAM configuration file.  
  
 \<Property Name="FileDropUNC">\\\\<computer name\>\alerts\</Property>  
  
 For appropriate steps to update the references, see [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).  
  
> [!IMPORTANT]
>  If you execute an update-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.  
  
 **Examples**  
  
```  
bm.exe update-config -FileName:MyConfig.xml  
```  
  
## get-changes Command  
 **Usage**  
  
 **bm.exe get-changes [ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Server:\<server>|Optional: The name of the server on which the BAM Primary Import database resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Gets a list of changes applied to the BAM Primary Import database. You can use this command to audit changes to the BAM Infrastructure. The command returns the following information:  
  
 The command type of the change and the file from which the change was applied.  
  
 Who applied the change.  
  
 Which activities were changed.  
  
 Which views were changed.  
  
 **Examples**  
  
```  
bm.exe get-changes  
```  
  
 Output of command  
  
 \#1: Deploy c:\bam\ordermanagement.xml  
  
 By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).  
  
 Activities: OrderMgmt  
  
 Views: SalesManager  
  
## get-defxml Command  
 **Usage**  
  
 **bm.exe get-defxml -FileName:\<output file>[ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|FileName:\<output file>|The path and name of the file to which to save the definitions.|  
|Server:\<server>|Optional: The name of the server from which to get the definitions. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database from which to get the definitions. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Retrieves all artifacts on from the BAM Primary Import database and saves them in a file as XML. The command will not overwrite existing files.  
  
 **Examples**  
  
```  
bm.exe get-defxml -FileName:BAMDefinition.xml  
bm.exe get-defxml -FileName:MyDef.xml -Server:MyServer -Database:MyPI  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)