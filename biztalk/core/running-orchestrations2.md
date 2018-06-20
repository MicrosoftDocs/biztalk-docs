---
title: "Running Orchestrations2 | Microsoft Docs"
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
  - "creating strong name keys"
  - "compiling orchestrations"
  - "host instances, stopping and restarting"
  - "deployment, orchestrations"
  - "orchestrations, compiling"
  - "orchestrations, deploying"
  - "stopping host instances"
  - "restarting host instances"
ms.assetid: a098d552-d302-44f6-9af9-d77d16549fd3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running Orchestrations
The following procedures describe how to build, deploy, bind, and start an orchestration.  
  
## Creating a Strong Name Key  
  
#### To create a strong name key  
  
1. Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt.  
  
2. Change directories to an existing project and press ENTER.  
  
    For example:  
  
    **\<drive\>:\Adapter_Install\biztalk\my_project**  
  
3. Type the following at the command prompt and press ENTER:  
  
    `sn -k SSOSchedule.snk`  
  
## Compiling and Deploying an Orchestration  
  
#### To compile and deploy an orchestration  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click the **SSOSchedule** project, and select **Properties**.  
  
2. Click **Common Properties**, and expand the **Assembly** node.  
  
3. Enter the path to SSOSchedule.snk in the **Assembly Key File** text box.  
  
4. Verify that Configuration Properties\Deployment\Server is a dot (.) or your computer name, and then click **OK**.  
  
5. In Solution Explorer, right-click **SSOSchedule**, and then click **Rebuild**.  
  
6. Right-click **SSOSchedule**, and then click **Deploy**.  
  
## Starting the Orchestration  
  
#### To start the orchestration  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**  
  
2. In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand the desired application, and then click **Orchestrations**.  
  
3. In the details pane, right-click the orchestration and click **Start**.  
  
## Stopping and Restarting a Host Instance  
 After you deploy the sample, you must restart the host instance.  
  
#### To stop and restart a host instance  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**  
  
2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.  
  
3. In the right pane, right-click the host instance (for example, the computer name), and click **Stop**.  
  
    The status of the host instance changes to **Stopped**.  
  
4. In the right pane, right-click the host instance and click **Start**.  
  
    The status of the host instance changes to **Start pending**.  
  
    To change the status to **Running** and click **Refresh**, or right-click the host instance and then click **Refresh**.  
  
## See Also  
 [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)