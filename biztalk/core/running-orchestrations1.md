---
title: "Running Orchestrations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strong name keys, creating"
  - "orchestrations"
  - "host instances, stopping and restarting"
  - "orchestrations, compiling"
  - "orchestrations, deploying"
ms.assetid: b992bdba-630d-4f28-aca8-c568f3c27968
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running Orchestrations
The following procedures describe how to build, deploy, bind, and start an orchestration.  
  
## Creating a Strong Name Key  
  
#### To create a strong name key  
  
1. Start a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.  
  
2. Change directories to an existing project, for example, \<drive\>:\Adapter_Install\biztalk2010\my_project.  
  
3. Type the following in the command prompt and press ENTER:  
  
    `sn -k SSOSchedule.snk`  
  
## Compiling and Deploying an Orchestration  
  
#### To compile and deploy an orchestration  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the SSOSchedule project, and select **Properties**.  
  
2. Click **Common Properties**, and expand the **Assembly** node.  
  
3. Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.  
  
4. Verify that Configuration Properties\Deployment\Server contains a dot (.) or your computer name, and click **OK**.  
  
5. In Solution Explorer, right-click **SSOSchedule**, and click **Rebuild**.  
  
6. Right-click the **SSOSchedule**, and click **Deploy**.  
  
## Starting the Orchestration  
  
#### To start the orchestration  
  
1.  In the BizTalk Administration console, select the orchestration you want to start.  
  
2.  Right-click the orchestration and click **Start**.  
  
## Stopping and Restarting a Host Instance  
 After deploying the sample, you must restart the host instance.  
  
#### To stop and restart a host instance  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and select **BizTalk Server Administration.**  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the **Microsoft BizTalk Server (local)** node, and expand **Hosts**.  
  
3. In the left pane, select the **BizTalkServerApplication**.  
  
4. In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.  
  
    The status of the host instance changes to **Stopped**.  
  
5. In the right pane, right-click the host instance and click **Start**.  
  
    The status of the host instance changes to **Start pending**.  
  
    To change the status to **Running**, click **Refresh**, or right-click the host instance and then click **Refresh**.  
  
## See Also  
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)