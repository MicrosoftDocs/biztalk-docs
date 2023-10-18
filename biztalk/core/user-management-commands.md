---
description: "Learn more about: User Management Commands"
title: "User Management Commands"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# User Management Commands
The BAM Management utility alert user management commands allow you to get, add, and remove users.  
  
-   get-accounts: Gets a list of all users and groups that can access a specified view.  
  
-   add-account: Grants access rights for the specified user or group to the specified view.  
  
-   remove-account: Removes access rights for a user or group from a specified view.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-accounts Command  
 **Usage**  
  
 **bm.exe get-accounts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The name of the view for which to list accounts.|  
|Server:\<server\>|Optional: The name of the server from which to retrieve the accounts. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which to retrieve the accounts. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists all users and groups that can access the specified view.  
  
 **Examples**  
  
 `bm.exe get-accounts -View:PurchaseOrder`  
  
 `bm.exe get-accounts -View:ShipmentOrder -Server:Ship -Database:ShipDatabase`  
  
## add-account Command  
 **Usage**  
  
 **bm.exe add-account -AccountName:\<account name\> -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|AccountName:<account name|The name of the account to which rights are granted.|  
|View:\<view name\>|The name of the view to which rights are granted.|  
|Server:\<server\>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Grants the specified user or group access rights to the specified view.  
  
> [!IMPORTANT]
>  If you are using Real Time Aggregations (RTAs), users added with **add-account** command are not automatically granted logon rights to SQL Server. If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs. Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import databases.  
  
 **Examples**  
  
```  
bm.exe add-account -AccountName:john -View:PurchaseOrder  
bm.exe add-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## remove-account Command  
 **Usage**  
  
 **bm.exe remove-account -AccountName:\<account name\> -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|AccountName:\<account name\>|The name of the account from which to remove rights to the view.|  
|View:\<view name\>|The name of the view to which rights are removed.|  
|Server:\<server\>|Optional: The name of the server on which the view resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the view resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes access rights for a user or group from a specified view. Removing an account from a view removes that account and all of its members from alerts defined for the specified view. If that account is the sole owner of an alert, the current user (admin) becomes the new owner of the alert.  
  
 **Examples**  
  
```  
bm.exe remove-account -AccountName:john -View:PurchaseOrder  
bm.exe remove-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
