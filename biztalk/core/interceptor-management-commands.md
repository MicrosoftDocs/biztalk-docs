---
title: "Interceptor Management Commands | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2be6460-1f81-4bc3-a831-34ff24d65d34
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor Management Commands
To support the new BAM interceptor functionality, four new commands have been added to the BAM Management utility.  
  
 These commands support the deployment, retrieval, and removal of interceptors. A command is also provided to list the configured interceptors.  
  
-   deploy-interceptor: Deploys an interceptor configuration.  
  
-   get-interceptorlist: Gets a list of activities on which interception is deployed.  
  
-   get-interceptor: Gets the interceptor configuration.  
  
-   remove-interceptor: Removes an interceptor configuration.  
  
> [!NOTE]
>  You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch. Using the Trace switch overrides the tracing settings in the configuration file. The switch can be used in conjunction with any normal BM command.  
  
> [!NOTE]
>  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## deploy-interceptor Command  
 **Usage**  
  
 **bm.exe deploy-interceptor -FileName:\<Configuration XML Filename\> [-Force:True ] [-Server:\<server\>] [-Database:\<database\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|FileName:\<Configuration XML Filename\>|The name of the XML file containing the interceptor configuration.|  
|Force:True|Optional: Forces deployment of the interceptor configuration when event source name collisions are detected.|  
|Server:\<server\>|Optional: The name of the server on which to deploy the interceptor. The server must be in the same domain as the computer from which you are running bm.exe.|  
|Database:\<database\>|Optional: The name of the BAM Primary Import database on which to configure the interceptor.|  
  
 This command deploys the interceptor configuration to the specified server and database. During deployment, the BAM Management utility performs the following validations:  
  
- XSD validation: The interceptor configuration is validated against the common interceptor configuration schema.  
  
- Validation that the activity exists (is deployed in the Primary Import database) and that checkpoints are valid (exist and have a matching data type).  
  
  If a collision is detected in the event source name, a warning is thrown describing the collision. In the case of a collision, the deployment will fail unless the **–Force:True** parameter flag is used.  
  
> [!NOTE]
>  The **–Force:True** parameter potentially removes interceptor configurations that reference event sources with the same name. You should use the **get-interceptor** command to create a backup of existing interceptor configurations before using the **–Force:True** parameter.  
  
 **Examples**  
  
```  
bm.exe deploy-interceptor  -FileName:myInceptor.xml  
bm.exe deploy-interceptor  -FileName:myInceptor.xml -Force:True  
```  
  
## get-interceptorlist Command  
 **Usage**  
  
 **bm.exe get-interceptorlist [-Server:\<server\>] [-Database:\<database\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Server:\<server\>|Optional: The name of the server from which to return a list of deployed interceptors. The server must be in the same domain as the computer from which you are running bm.exe.|  
|Database:\<database\>|Optional: The name of the BAM Primary Import database from which to retrieve the deployed interceptors.|  
  
 This command returns a list of the activities, and their associated event sources, for which interception is enabled.  
  
 **Example**  
  
```  
bm.exe get-interceptorlist   
```  
  
## get-interceptor Command  
 **Usage**  
  
 **bm.exe get-interceptor [-Server:\<server\>] [-Database:\<database\>] -FileName: \<Configuration XML Filename\> [ -Activity: \<Activity Name\>] [-EventSource: \<Event Source Name\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Server:\<server\>|Optional: The name of the server from which to retrieve the deployed interceptor. The server must be in the same domain as the computer from which you are running bm.exe.|  
|Database:\<database\>|Optional: The name of the BAM Primary Import database from which to retrieve deployed interceptor.|  
|FileName:\<Configuration XML Filename\>|The name of the XML file to which to write the interceptor configuration.|  
|Activity:\<Activity Name\>|Optional: Specifies the activity for which to return the configured interceptor. Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.|  
|EventSource:\<Event Source Name\>|Optional: Specifies the event source for which to return the configured interceptor. Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.|  
  
 If no activity name or event source name is provided, the command returns a valid configuration file containing the interceptor configurations for all event sources and activities.  
  
 If only an activity name is provided, the command returns a valid interceptor configuration file for all event sources for that activity.  
  
 If only an event source name is provided, the command returns a valid interceptor configuration file for that event source across all activities.  
  
 If both an activity name and an event source name are provided, then the command returns a valid interceptor configuration file for that event source for that activity.  
  
 **Examples**  
  
```  
bm.exe get-interceptor   
bm.exe get-interceptor  -Activity:ShippingPO  
```  
  
## remove-interceptor Command  
 **Usage**  
  
 **bm.exe remove-interceptor [-Server:\<server\>] [-Database:\<database\>] [ -Activity: \<Activity Name\>][-EventSource: \<Event Source Name\>]**  
  
 **Parameters**  
  
|Parameter|Description|  
|---------------|-----------------|  
|Server:\<server\>|Optional: The name of the server on which the interceptor is configured. The server must be in the same domain as the computer from which you are running bm.exe.|  
|Database:\<database\>|Optional: The name of the database on which the interceptor is configured.|  
|Activity: \<Activity Name\>|Optional: Specifies the activity for which to remove the specified interceptor. Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.|  
|EventSource: \<Event Source Name\>|Optional: Specifies the event source for which to remove the specified interceptor. Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.|  
  
 If only an activity name is provided, the command removes the interceptor for all event sources for that activity.  
  
 If only an event source name is provided, the command removes only that event source portion for all activities.  
  
 **Example**  
  
```  
bm.exe remove-interceptor   
```  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)