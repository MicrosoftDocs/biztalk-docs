---
description: "Learn more about: Database Commands"
title: "Database Commands"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Database Commands
The BAM Management utility database commands allow you to work with the BAM databases:  
  
-   setup-databases: Creates the BAM-specific databases.  
  
-   migrate-sql: Migrates your BAM databases from:  
  
    -   Microsoft SQL Server 2000 to Microsoft SQL Server 2008  
  
    -   Microsoft SQL Server 2005 to Microsoft SQL Server 2008  
  
-   enable-reference: Enables a reference to a distributed BAM Primary Import database.  
  
-   get-references: Gets a list of references to distributed BAM Primary Import databases.  
  
-   disable-reference: Disables a reference to a BAM Primary Import database.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## setup-databases Command  
 **Usage**  
  
 **bm.exe setup-databases-ConfigFile:\<configuration file\>[ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|ConfigFile:\<configuration file\>|The BAM configuration file from which to create the database.|  
|NSUser:\<notifications service user name\>|Optional: The user ID of a notifications services user with permissions to create databases.|  
|NSUserPassword|Optional: The password for the specified notifications services user.|  
  
 Creates the databases described in the configuration file (BAM Primary Import, BAM Star Schema, BAM Archive, BAM Analysis, and alerts) if they do not already exist. Once the databases are created, the command creates the associated BAM metadata tables and stored procedures.  
  
 The NSUser and NSUserPassword parameters are required if you are setting up BAM alerts. If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.  
  
> [!NOTE]
>  After the completion of the command, you may note an exception from the AlertModule in the trace log:  
>   
>  "The specified account is the Database Owner. The Database owner always has access to the view and cannot be added to or removed from the view."  
>   
>  In addition, you may see a warning in the event from NotificationServices #19001.  
>   
>  If no errors were reported during the execution of the command, you can safely disregard these notices.  
  
> [!IMPORTANT]
>  If you execute a setup-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.  
  
 To set up the BAM databases you must have administrator permissions on the Microsoft SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases. To set up SQL Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.  
  
 **Examples**  
  
```  
bm.exe setup-databases -ConfigFile:BamConfiguration.xml  
bm.exe setup-databases -ConfigFile:cfg.xml -NSUser:domain\user1  
```  
  
## migrate-sql Command  
 **Usage**  
  
 **bm.exe migrate-sql -From:sql2000 -To:sql2008 [ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 \- Or -  
  
 **bm.exe migrate-sql -From:sql2005 -To:sql2008 [ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|From: sql2000|Specifies that you are converting from a Microsoft SQL Server 2000 database.|  
|To:sql2008|Specifies that you are converting to a Microsoft SQL Server 2008 database.|  
|From: sql2005|Specifies that you are converting from a Microsoft SQL Server 2005 database.|  
|To:sql2008|Specifies that you are converting to a Microsoft SQL Server 2008 database.|  
|NSUser:\<notifications service user name\>|Optional: The user ID of a Notifications Services user with permissions to create databases.|  
|NSUserPassword|Optional: The password for the specified Notifications Services user.|  
|Server:\<server\>|Optional: The name of the server on which the converted database will reside. The server must be in the same domain as the computer hosting the Microsoft SQL Server 2008 database. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: Then name of the converted database. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Migrates the BAM infrastructure from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008. Use this command after you upgrade your database server and Analysis server from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008.  
  
 The NSUser and NSUserPassword parameters are required if BAM alerts are configured. If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.  
  
 To migrate the SQL Server Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.  
  
> [!NOTE]
>  If you receive the error message "ERROR: Cannot start service NS$BAMAlerts on computer '\<computer name\>'. The service did not respond to the start or control request in a timely fashion.", try restarting the service manually. If the SQL Server is extremely busy during a migration, the service may not restart.  
  
> [!NOTE]
>  To run the migrate-sql command on the computer where Notification Services is installed, you must belong to the Local Administrators group on that computer.  
  
 **Examples**  
  
```  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
```  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
## enable-reference Command  
 **Usage**  
  
 **bm.exe enable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|TargetServer:\<target server\>|The name of the server to which the reference is enabled. The server must be in the same domain as the computer from which you are running bm.exe.|  
|TargetDatabase:\<target database\>|The name of the database to which the reference is enabled.|  
|Server:\<server\>|Optional: The name of the server which will have a reference enabled to the target server and database. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database which will have a reference enabled to the target server and database. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Enables a reference to another distributed BAM Primary Import database. This allows subscriptions from the current database to the view and activity metadata on the target BAM Primary Import database. You use this to enable navigation of the distributed activities.  
  
 You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.  
  
 **Examples**  
  
```  
bm.exe enable-reference -TargetServer:MySrv -TargetDatabase:BamPrimaryImport  
bm.exe enable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## get-references Command  
 **Usage**  
  
 **bm.exe get-references [ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Server:\<server\>|Optional: The name of the server on which to get a list of references. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which to get a list of references. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists the references enabled on the computer on which the command is executed.  
  
 **Examples**  
  
```  
bm.exe get-references  
bm.exe get-references -Server:MyServer -Database:MyPrimaryImport  
```  
  
## disable-reference Command  
 **Usage**  
  
 **bm.exe disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|TargetServer:\<target server\>|The name of the server on which to disable the references. The server must be in the same domain as the computer from which you are running bm.exe.|  
|TargetDatabase:\<target database\>|The name of the database on which to disable the references.|  
|Server:\<server\>|Optional: The name of the server on which references to the target server and database are to be disabled. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which references to the target server and database are to be disabled. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Disables a reference to another distributed BAM Primary Import database on the target server.  
  
 You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.  
  
 **Examples**  
  
```  
bm.exe disable-reference -TargetServer:MySrv -TargetDatabase:BamPI  
bm.exe disable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
