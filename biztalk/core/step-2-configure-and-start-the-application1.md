---
title: "Step 2: Configure and Start the Application1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Configure and Start the Application
![Step 2 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Time to complete:** 10 minutes  
  
 **Objective:** In this step, you configure and start the EAISolution application.  
  
 **Purpose:** The configuration is mostly about binding.  A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party. This enables communication between different components of a BizTalk business solution. You can create bindings by using the BizTalk Server Administration console.  
  
## Prerequisites  
 Note the following requirements before you begin this step:  
  
- Before you begin this step you must complete [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md).  
  
- You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
## Procedures  
 The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions. A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.  For more information, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md).  In [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md), we configure the application name to be “EAISolution” before we deploy the projects.  So the EAISolution application contains the orchestration, the two schema, and the map.  
  
#### To open the EAISolution application from BizTalk Server Administration Console  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2. In the console tree on the left side of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.  
  
3. Expand **BizTalk Group**, expand **Applications**, and then click **EAISolution**.  
  
   In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), we created an orchestration.  In the orchestration, we defined the logical ports.  In the following procedures, you will define the physical ports and bind the physical ports to the logical ports.  
  
#### To create the ReceiveRequest port  
  
1.  From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2.  On the General tab,  do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **EAISolutionReceiveRequestPort**.|  
    |**Enable routing for failed messages**|(clear)|  
  
3.  Click **Receive Locations**, and then click **New**.  
  
4.  From Receive Location1 – Receive Location Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **EAISolutionReceiveRequestLocation**.|  
    |**Type**|Select **File**.|  
    |**Receive handler**|Select **BizTalkServerApplication**.|  
    |**Receive pipeline**|Select **XMLReceive**.|  
  
5.  Click **Configure**.  
  
6.  From File Transport Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Receive folder**|Type **C:\BTSTutorials\WareHouse\Request**.|  
  
7.  Click **OK** three times.  
  
#### To create the SendDecline port  
  
1.  From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
2.  On the General tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **EAISolutionSendDeclinePort**.|  
    |**Type**|Select **File**.|  
    |**Send handler**|Select **BizTAlkServerApplication**.|  
    |**Send pipeline**|Select **XML Transmit**.|  
  
3.  Click **Configure**.  
  
4.  From File Transport Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Receive folder**|Type **C:\BTSTutorials\WareHouse\RequestDecline**.|  
    |**File name**|Type **RequestDecline_%MessageID%.xml**.|  
  
5.  Click **OK** twice.  
  
#### To create the SendToERP port  
  
1.  From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
2.  On the General tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **EAISolutionSendToERPPort**.|  
    |**Type**|Select **File**.|  
    |**Send handler**|Select **BizTAlkServerApplication**.|  
    |**Send pipeline**|Select **XML Transmit**.|  
  
3.  Click **Configure**.  
  
4.  From File Transport Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Receive folder**|Type **C:\BTSTutorials\ERP\Request**.|  
    |**File name**|Type **Request_%MessageID%.xml**.|  
  
5.  Click **OK** twice.  
  
#### To bind the ports  
  
1.  From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Configure**.  
  
2.  From Configure Application, in the left pane, click **EAIProcess**.  This is the orchestration we created.  
  
3.  From the right pane, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Host**|Select **BizTalkServerApplication**.|  
    |**Receive Port** for **ReceiveRequestPort**|Select **EAISolutionReceiveReqeustPort**.|  
    |**Send PortsSend Port Groups** for **ReceiveRequestPort**|Select **EAISolutionSendDeclinePort**.|  
    |**Receive Port** for **ReceiveRequestPort**|Select **EAISolutionSendToERPPort**.|  
  
4.  Click **OK** to save the configuration.  
  
#### To start the application  
  
1.  From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Start**.  
  
2.  From the dialog, click **Start**.  
  
## What did I just do?  
 In this step, you configured and started the EAIApplication application.  
  
## Next Steps  
 You test how the EAI solution processes messages in [Step 3: Test the Solution](../core/step-3-test-the-solution2.md).  
  
## See Also  
 [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md)   
 [Step 3: Test the Solution](../core/step-3-test-the-solution2.md)