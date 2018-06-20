---
title: "Install the Adapter into BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1164468d-75a9-4116-87a6-6055948c198b
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install the Adapter into BizTalk Server
After the proper [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] entries have been written to the registry the adapter must be added to the BizTalk Management database. After the adapter is added to this database it is an actively configured adapter and can process messages when it is properly configured. You install the adapter into the database by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. After installing the adapter in the database, restart the host instance.  

> [!NOTE]
>  To be visible for addition in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, an adapter must be properly registered in the HKLM registry and must implement the necessary adapter interfaces.  

### To install the static sample adapter  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.  

3. Expand **Platform Settings** and select **Adapters**.  

4. Right-click **Adapters**, click **New**, and then click **Adapter**.  

5. In the **Adapter Properties** dialog box, do the following.  


   |  Use this   |                      To do this                       |
   |-------------|-------------------------------------------------------|
   |    Name     |                   Type **Static**.                    |
   |   Adapter   | Select **Static DotNetFile** from the drop-down list. |
   | Description |            Type **Sample Static Adapter**.            |


6. Click **OK**.  

    The static adapter now appears in the list of adapters in the right window of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

### To stop and restart the host instance  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, double-click the  **BizTalk Group** node.  

3. Expand **Platform Settings**, select **Hosts**, and then select **BizTalkServerApplication** in the results pane.  

4. Right-click the host instance (typically, the computer name), and then click **Stop**.  

    The status of the host instance changes to **Stopped**.  

5. In the results pane, right-click the host instance, and then click **Start**.  

    The status of the host instance changes to **Start pending**. You must click **Refresh**, or right-click the host instance and then click **Refresh**, to change the status to **Running**.