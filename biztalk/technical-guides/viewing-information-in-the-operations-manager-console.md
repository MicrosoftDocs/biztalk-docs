---
description: "Learn more about: Viewing Information in the Operations Manager Console"
title: "Viewing Information in the Operations Manager Console | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6acdf425-4c36-4d89-9493-81b33481fe6d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Viewing Information in the Operations Manager Console
Use the views provided with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack to understand the current availability, configuration, health, and performance of your BizTalk Server environment. A view can contain a lengthy list of objects. To find a specific object or group of objects, you can use the Scope, Search, and Find buttons on the Operations Manager toolbar. For more information, see the How to Manage Monitoring Data Using Scope, Search, and Find topic in Operations Manager 2007 R2\2012 Help.  
  
 The following views are listed directly under **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** node in the Monitoring pane of the Operations Console.  
  
-   **Application Views**: A BizTalk administrator is interested in monitoring the state and health of various BizTalk Server artifacts and applications such as orchestrations send ports, receive locations, and so on.  
  
-   **Deployment Views**: An enterprise IT administrator is interested in monitoring the state and health of the various enterprise deployments the machines hosting the SQL Server databases, machines hosting the SSO service, host instance machines, IIS, network services, and so on.  
  
## Application Views  
 Application views contain the elements described in the following table.  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|Application State View|This is a dashboard view that displays the health of a BizTalk application. The health of BizTalk application depends on the health of its constituent artifacts such as Orchestrations, Send Port Group, Send Port, Receive Port, and Receive Location. The Details View pane provides the properties of the hosted BizTalk application.|  
|Group State View|This is a dashboard view that displays the health of a BizTalk group. The health of a BizTalk group depends on the health of BizTalk host and BizTalk applications. The Details View pane provides the properties of the BizTalk group.|  
|Host State View|This is a dashboard view that displays the health of a BizTalk host. The health of a BizTalk host depends on the health of the instances of the hosted BizTalk applications. The Details View pane provides the properties of the BizTalk host.|  
  
#### Application Artifacts Views  
 Application artifacts views contain the elements described in the following table.  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|Orchestrations State View|Displays the configuration and runtime state of Orchestration for the hosted application.|  
|Receive Location State View|Displays the configuration and runtime state of Receive Location for the hosted application.|  
|Receive Ports State View|Displays the configuration and runtime state of Receive Ports for the hosted application.|  
|Send Port Groups State View|Displays the configuration and runtime state of Send Port Group for the hosted application.|  
|Send Port State View|Displays the configuration and runtime state of Send Port for the hosted application.|  
  
## Deployment Views  
 Deployment views contain the elements described in the following table.  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|Deployment State View|This is a dashboard view that displays the health of a BizTalk deployment group. The health of the BizTalk deployment group depends on the health of its constituent runtime server components such as BAM Role, Rule Engine Role, BizTalk Run-time Role and BizTalk Host. The Details View pane provides the properties of the BizTalk deployment group.|  
|Hosts State View|This is a dashboard view that displays the health of a BizTalk host. The health of a BizTalk host depends on the health of the instances of the hosted BizTalk applications. The Details View pane provides the properties of the BizTalk host.|  
|Rule Engine Role State View|This is a dashboard view that displays the health of a Rule Engine service that is running on the runtime servers. The Details View pane provides the properties of the runtime servers that have Rule Engine service installed.|  
|Runtime Role State View|This is a dashboard view that displays the health of the runtime servers that have runtime rule engine service installed. The health of a BizTalk Run-time Role depends on the health of its components such as SSO Service, management database, message box database, SSO database and tracking database. The Details View pane provides the properties of the runtime servers.|  
  
### BAM Component Views  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|BAM Alerts State View|Displays the state view of BizTalk BAM alerts component.|  
|BAM Analysis State View|Displays the state view of BizTalk BAM analysis component.|  
|BAM Performance View|The Legend pane displays the performance counter for BAM.|  
|BAM Portal State View|Displays the state view of BAM portal.|  
|BAM Run-time State View|Displays the state view of BAM run-time.|  
  
#### BAM Alerts  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|BAM Alerts State View|Displays a list of BizTalk BAM alerts which is a notification service and generated when any of the critical services are unavailable.|  
  
##### Runtime Component Views  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|Application Service State View|Displays the health of all host instances in a BizTalk group.|  
|Message Box Performance State View|The Legend pane displays the performance counter for Message Box Tracking Data Size.|  
|Messaging Adapters Performance View|The Legend pane displays the performance counter for MSMQ Receive Adapter Bytes Received.|  
|Messaging Performance View|The Legend pane displays the performance counter for Active Receive Locations.|  
|Orchestration Performance View|The Legend pane displays the performance counter for Runnable Orchestrations.|  
|Server Resource Usage View|The Legend pane displays the performance counter for Physical Disk Percentage Idle Time.|  
  
###### Runtime Alerts  
  
### Elements  
  
|View Name|Description|  
|---------------|-----------------|  
|Core Alerts View|Displays BizTalk core alerts.|  
|Messaging Alerts View|Displays BizTalk messaging alerts.|
