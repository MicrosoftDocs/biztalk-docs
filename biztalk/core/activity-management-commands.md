---
description: "Learn more about: Activity Management Commands"
title: "Activity Management Commands | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34db54f3-4116-49de-880b-c9891a38d2e7
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Activity Management Commands
The BAM Management utility activity management commands allow you to work with deployed activities.  
  
-   get-activities: Gets a list of deployed activities.  
  
-   remove-activity: Removes an activity.  
  
-   get-activitywindow: Gets the duration for an activity.  
  
-   set-activitywindow: Sets the activity duration for an activity.  
  
-   get-index: Gets the list of indexes.  
  
-   create-index: Creates a new index.  
  
-   delete-index: Deletes an index.  
  
-   get-archive: Gets the behavior of archived activity.  
  
-   set-archive: Sets the behavior of archived activity.  
  
> [!NOTE]
>  You can enable tracing on any BAM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BAM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-activities Command  
 **Usage**  
  
 **bm.exe get-activities [ -View:\<view name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Name:\<activity name\>|The name of the activity to remove.|  
|Server:\<server\>|Optional: The name of the server from which to get the list of activities. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which to get the list of activities. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists the activities deployed on the computer on which the command is executed.  
  
 **Examples**  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## remove-activity Command  
 **Usage**  
  
 **bm.exe remove-activity -Name:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Name:\<activity name\>|The name of the activity to remove.|  
|Server:\<server\>|Optional: The name of the server from which to remove the activity. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which to remove the activity. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes the specified activity from the BAM Primary Import database. If the activity has dependent views, the command will fail and report an error. Use the remove-view command to remove all the dependent views and execute the remove-activity command again.  
  
 **Examples**  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## get-activitywindow Command  
 **Usage**  
  
 **bm.exe get-activitywindow -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the .activity.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Displays the duration for the specified activity. The command returns the length of the duration and the units by which the duration is measured.  
  
 **Examples**  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## set-activitywindow Command  
 **Usage**  
  
 **bm.exe set-activitywindow -Activity:\<activity name\> -TimeLength:\<integer number\> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the activity.|  
|TimeLength:\<integer number\>|The duration for the activity.|  
|TimeUnit:Month&#124;Day&#124;Hour&#124;Minute|The unit measure for the duration.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Sets the duration for the specified activity.  
  
 **Examples**  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## get-index Command  
 **Usage**  
  
 **bm.exe get-index -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the activity.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists all the indexes that have been created for the specified activity.  
  
 **Examples**  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## create-index Command  
 **Usage**  
  
 **bm.exe create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|IndexName:\<index name\>|The name of the new index.|  
|Activity:\<activity name\>|The name of the activity for which the index is created.|  
|Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...]|A comma-delimited list of checkpoints for the index.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Creates an index for the specified activity using the specified checkpoints.  
  
 **Examples**  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## delete-index Command  
 **Usage**  
  
 **bm.exe delete-index -IndexName:\<index name\> -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|IndexName:\<index name\>|The name of the index to delete.|  
|Activity:\<activity name\>|The name of the activity for which the index is deleted.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Deletes the specified index with the given name from the specified activity.  
  
 **Examples**  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## get-archive Command  
 **Usage**  
  
 **bm.exe get-archive -Activity:\<activity\> [-Server:\<server\>] [-Database:\<database\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the activity for which the behavior is to be displayed.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Gets the behavior of the archiving package for the specified activity, whether the archiving package will archive orpurge activity data.  
  
 **Examples**  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## set-archive Command  
 **Usage**  
  
 **bm.exe set-archive -Activity:\<activity\> -ShouldArchive:True [-Server:\<server\>] [-Database:\<database\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the activity for which the behavior is to be displayed.|  
|ShouldArchive: True|If set to True, the activity is moved to Archive DB. If set to False, the activity is purged.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Sets the behavior of the archiving package for the activity specified so that activity data is moved into the Archive DB. By default, this behavior is set for new activities that are deployed.  
  
 **Examples**  
  
 To purge the BAM activity data, execute the following:  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 To move the BAM activity data to the BAMArchive database, execute the following:  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
