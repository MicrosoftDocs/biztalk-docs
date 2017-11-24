---
title: "BAM Command-Line Script for Notification Services Configuration Files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aa4a460-58f9-439d-af28-0a9cb2288236
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Command-Line Script for Notification Services Configuration Files
Administrators use the ProcessBamNSFiles.vbs script to customize the behavior of SQL Server Notification Services for BAM alerts. You can use the script to obtain the Notification Services application definition file (ADF) and Notification Services configuration file. These files can be modified and then the script can be used to apply the changes.  
  
 You run the script from a Notification Services command prompt and not from a typical command prompt. Running the script from a typical command prompt will cause the script to execute incorrectly. When running the script all parameters are mandatory.  
  
## Get command  
 **Usage**  
  
 **cscript ProcessBamNSFiles -Get \<configuration file path\> \<ADF file path\>  \<primary import server\> \<primary import database\>**  
  
|Parameter|Description|  
|---------------|-----------------|  
|configuration file path|Specifies the name and location in which to store the configuration file.|  
|ADF file path|Specifies the name and location in which to store the ADF file.|  
|primary import server|Name of the computer on which the BAM Primary Import database is stored.|  
|primary import database|Name of the BAM Primary Import database.|  
  
 Retrieves the Notification Services configuration and application definition files from the BAM Primary Import database and saves them to specified paths.  
  
## Update command  
 **Usage**  
  
 **cscript ProcessBamNSFiles -Update \<configfilepath\> \<adffilepath\>  \<primaryimport server\> \<primary import db\>**  
  
|Parameter|Description|  
|---------------|-----------------|  
|configuration file path|Specifies the name and location from which to update the Notification Services configuration information.|  
|ADF file path|Specifies the name and location from which to update the ADF information.|  
|primary import server|Name of the computer on which the BAM Primary Import database is stored.|  
|primary import database|Name of the BAM Primary Import database.|  
  
 Calls Notification Services and updates the settings with the information in the specified files. The configuration and ADF files are stored in the BAM Primary Import database.  
  
## See Also  
 [BAM Command-Line Tools](../core/bam-command-line-tools.md)