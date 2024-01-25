---
description: "Learn more about: Deployment of BAM Definition (Observation Model) Commands"
title: "Deployment of BAM Definition (Observation Model) Commands"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Deployment of BAM Definition (Observation Model) Commands
The BAM management utility deployment commands allow you to apply, modify, and remove definitions.  
  
-   deploy-all: Deploys a BAM definition.  
  
-   update-all: Updates a BAM definition.  
  
-   remove-all: Removes a BAM definition.  
  
-   update-livedataworkbook: Updates the database connection information in a live data workbook.  
  
-   regenerate-livedataworkbook: Regenerates the live data workbook on the server.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## deploy-all Command  
 **Usage**  
  
 **bm.exe deploy-all -DefinitionFile:\<def file\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def file\>|The path and name of the file containing the definitions to deploy.|  
|Server:\<server\>|Optional: The name of the server to which to deploy the definitions. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database to which to deploy the definitions. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Deploys all artifacts from the specified BAM definition XML file to the specified server and database. The file can be a text file containing the BAM definition XML or a BAM Excel workbook. The definition file must include only new artifacts. If the file contains artifacts that have already been deployed, the deployment will fail and report an error.  
  
 **Considerations for deploying BAM definitions**  
  
 When deploying alert subscriptions, user IDs of the subscribers must be specified in a domain\user format.  
  
 The distributed transaction coordinator (DTC) service must be running on the computer on which the **deploy-all** command is issued.  
  
 When deploying a definition the BAM Management utility only supports 14 dimension levels in Real-Time Aggregation (RTA) view. Deploying additional levels returns a Deployment failed error.  
  
 If you define multiple views that use different language settings and deploy your solution to a server that uses a single language, the views will be undeployable. This scenario is supported only in a case where you don't have scheduled aggregations that require OLAP as part of the BAM definition.  
  
 The BAM management utility limits you to 49 deployed activity views when BAM Alerts are enabled. The number of activity views is calculated as the Summation 1..N of View(n) multiplied by the number of parent activities.  For example, if you deploy a view that is based on two activities, you get two activity views.  If you deploy two views, one of which spans two activities and the other based on a single activity, you have 3 activity views.  
  
 The BAM Management utility blocks deployment of BAM definitions which have multiple PivotTable reports which are defined on the same RTA and cube name combination. Bm.exe will terminate the deployment and return the following error:  
  
 Deploying View... ERROR: The BAM deployment failed.  
  
 Only one PivotTable view can be defined on a given RTA and cube.  
  
 The following list of names are reserved and will cause the definition deployment to fail:  
  
-   RecordID  
  
-   ActivityID  
  
-   IsVisible  
  
-   IsComplete  
  
-   LastModified  
  
> [!NOTE]
>  If bm.exe encounters an error during the deployment, the deployment is terminated and changes to the views and activities are rolled back. Changes to OLAP cubes are not rolled back since OLAP does not support transactional deployment.  
  
> [!NOTE]
>  BAM definitions created on a computer using one locale setting cannot be deployed to a computer configured with a different locale setting. For example, a BAM definition generated using an English language version of Microsoft Excel on a computer configured with a EN locale setting cannot be deployed on a computer configured for Japanese using a JA locale setting.  
  
 **Examples**  
  
```  
bm.exe deploy-all -DefinitionFile:MyDef.xml  
bm.exe deploy-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## update-all Command  
 **Usage**  
  
 **bm.exe update-all -DefinitionFile:\<def file\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def file\>|The path and name of the file containing the definitions from which to perform the update.|  
|Server:\<server\>|Optional: The name of the server to which to deploy the definition updates. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database to which to deploy the definition updates. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Updates certain artifacts from the BAM definition XML. The file can be a text file containing the BAM definition XML or a BAM Excel workbook. The update does not delete artifacts that are not described in the current definition file. It can add new checkpoints to activities, but cannot drop checkpoints from deployed activities. The update can neither rename checkpoints nor change checkpoint properties.  
  
 Once an activity has been deployed, the actions you can take on an activity become restricted. Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them. This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.  
  
> [!NOTE]
>  You cannot use this command to add new activities to an existing view. To add a view to an activity you must create a new view that includes the new activity. You can then undeploy the old view, but be aware that you will then lose your OLAP data history.  
  
 **Examples**  
  
```  
bm.exe update-all -DefinitionFile:MyDef.xml  
bm.exe update-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## remove-all Command  
 **Usage**  
  
 **bm.exe remove-all DefinitionFile:\<def file\> [ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|DefinitionFile:\<def file\>|The path and name of the file containing the definitions to remove.|  
|Server:\<server\>|Optional: The name of the server from which the definitions will be removed. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database from which the definitions will be removed. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Removes all artifacts specified in the BAM definition XML file. The file can be a text file containing the BAM definition XML or a BAM Excel workbook. The definition for each artifact must exactly match the original definition that was used for deployment.  
  
 **Examples**  
  
```  
bm.exe remove-all -DefinitionFile:MyDef.xml  
bm.exe remove-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## update-livedataworkbook Command  
 **Usage**  
  
 **bm.exe update-livedataworkbook -Name:\<livedata workbook file name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Name:\<livedata workbook\>|The name of the existing live workbook to update.|  
|Server:\<server\>|Optional: The name of the server on which the workbook resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the workbook resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Updates the BAM Primary Import database connection information in the specified BAM live data workbook.  
  
> [!NOTE]
>  When configuring new connection string, you must restart the TDDS service to ensure that the service recognizes the change. For more information on the TDDS service, see [BAM Event Bus Service Stored Procedures](../core/bam-event-bus-service-stored-procedures.md).  
  
 **Examples**  
  
```  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls -Server:SalesSrv  
```  
  
## regenerate-livedataworkbook Command  
 **Usage**  
  
 **bm.exe regenerate-livedataworkbook -WorkbookName:\<livedata workbook file name\>[ -Server:\<server\> ][ -Database:\<database\> ]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|WorkbookName:\<livedata workbook file name\>|The name of the workbook to update.|  
|Server:\<server\>|Optional: The name of the server on which the workbook resides. The server must be in the same domain as the computer from which you are running bm.exe. If the server name is not specified, bm.exe uses the default name of localhost.|  
|Database:\<database\>|Optional: The name of the database on which the workbook resides. If the name is not specified, bm.exe uses the default name BamPrimaryImport.|  
  
 Generates a BAM live data workbook but does not deploy the workbook.  
  
 Examples  
  
```  
bm.exe regenerate-livedataworkbook -WorkbookName:SalesManager_Live.xls  
bm.exe regenerate-livedataworkbook -WorkbookName:SM_Live.xls -Server:S1  
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)
