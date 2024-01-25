---
description: "Learn more about: View Management Commands"
title: "View Management Commands"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# View Management Commands
The BAM Management utility view management commands allow you to work with deployed views.  
  
-   get-views: Lists all the deployed views.  
  
-   remove-view: Removes a deployed view.  
  
-   get-rtawindow: Gets the duration on a view.  
  
-   set-rtawindow: Sets the duration on a view.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## get-views Command  
 **Usage**  
  
 **bm.exe get-views [ -Activity:\<activity name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Activity:\<activity name\>|The name of the activity from which to list the views.|  
|Server:\<server\>|Optional: The name of the server from which to get the list of views. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which to get the list of views. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Lists the views deployed on the computer on which the command is executed.  
  
 **Examples**  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## remove-view Command  
 **Usage**  
  
 **bm.exe remove-view -Name:\<view name\> [ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Name:\<view name\>|The name of the view to remove.|  
|Server:\<server\>|Optional: The name of the server from which to remove the view. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which to remove the view. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes the specified view from the BAM Primary Import database. If the view has dependent alerts, they are removed at the same time.  
  
 **Examples**  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## get-rtawindow Command  
 **Usage**  
  
 **bm.exe get-rtawindow -View:\<view name\> -Activity:\<activity name\> -Rta:\<RTA name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The view name.|  
|Activity:\<activity name\>|The activity name.|  
|Rta:\<RTA name\>|The real-time aggregation name.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Displays the duration of the specified real-time aggregation. The command returns the length of the duration and the units by which the duration is measured.  
  
 **Examples**  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## set-rtawindow Command  
 **Usage**  
  
 **bm.exe set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\>-TimeUnit:Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|View:\<view name\>|The view name.|  
|Activity:\<activity name\>|The activity name.|  
|Name:\<RTA name\>|The real-time aggregation name.|  
|TimeLength:\<integer number\>|The duration for the real-time aggregation.|  
|TimeUnit:Month&#124;Day&#124;Hour&#124;Minute|The unit measure for the window duration.|  
|Server:\<server\>|Optional: The name of the server on which the activity resides. The server must be in the same domain as the machine from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the activity resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Sets the duration for the specified real-time aggregation.  
  
 **Examples**  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
