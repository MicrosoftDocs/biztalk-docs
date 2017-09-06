---
title: "Alert Management Commands | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a96d8de7-a918-4737-aa35-4e1abf6bb08f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Alert Management Commands
The BAM management utility alert management commands allow you to work with deployed alerts.  
  
-   get-alerts: Get a list of deployed alerts.  
  
-   remove-alerts: Removes an alert.  
  
-   enable-alerts: Enables alerts on a view.  
  
-   disable-alerts: Disables alerts on a view.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-alerts Command  
 **Usage**  
  
 **bm.exe get-alerts [ -View:\<view name> ][ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name>|The name of the view from which to get the list of alerts.|  
|Server:\<server>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists the alerts defined on the computer on which the command is executed.  
  
 **Examples**  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## remove-alerts Command  
 **Usage**  
  
 **bm.exe remove-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name>|The name of the view from which to remove alerts.|  
|Server:\<server>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes all alerts on the specified view.  
  
 **Examples**  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## enable-alerts Command  
 **Usage**  
  
 **bm.exe enable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name>|The name of the view on which to enable alerts.|  
|Server:\<server>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Enables alerts on the specified view.  
  
 **Examples**  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## disable-alerts Command  
 **Usage**  
  
 **bm.exe disable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name>|The name of the view on which to disable alerts.|  
|Server:\<server>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Disables alerts on the specified view.  
  
 **Examples**  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)