---
title: "Deploy and test the application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2c86d5f-1849-4b7d-8061-23f156245f5b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploy and test the application
> [!NOTE]
>  This tutorial applies to BizTalk Server only.  
  
 In this topic, we build, deploy, configure, and test the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  
  
## Build and deploy the application  
  
1.  In the Solution Explorer, right-click the BizTalk project name, and then click **Properties**.  
  
2.  On the Property page, click the Signing tab, select the Sign the assembly check box, and from the drop-down choose the option to create a new strong name key file. Follow the prompts to create the file.  
  
3.  Save changes to the project. In Solution Explorer, right-click the solution name, and then click **Build Solution**.  
  
4.  After project builds successfully, in the Solution Explorer, right-click the solution name, and then click **Deploy Solution**.  
  
## Configure the application  
 To configure the application, in [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], create the send and receive ports and then bind them to the orchestration and the logical send/receive ports created as part of the orchestration.  
  
1. Create a receive port through which a JSON purchase order is received by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  
  
   1. In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
   2. Provide a name for the receive port, and then from the left pan, click **Receive Locations**. In the **Receive Locations** tab, click **New**.  
  
   3. Specify a name for the receive location, select the port type as **FILE**, and then click **Configure**.  
  
   4. Provide the folder location from where the receive location will pick the incoming JSON purchase order. Specify `*.json` as the file mask and then click **OK**.  
  
   5. From the **Receive Pipeline** drop-down, select **JSONToXml**. You created this custom receive pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. Right-click the ellipsis **(…)** button next to the pipeline, and then under **Stage 1 – Deocde Component**, provide the following values:  
  
      - RootNode - `ROOT`  
  
      - RootNodeNamespace –`http://BTSJSON`.  
  
        These values represent the target namespace and the root node name of the XML purchase order schema that was generated from the JSON purchase order using the JSON schema wizard.  
  
   6. Click **OK** until you exit all open dialog boxes.  
  
2. Create a send port for sending out JSON invoice messages.  
  
   1. In [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Application 1**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
   2. Specify a name for the send port, select the port type as **FILE**, and then click **Configure**.  
  
   3. Provide the folder location where the send port copies the outgoing JSON invoice. Specify `%MessageID%.json` as the file name and then click **OK**.  
  
   4. From the **Send Pipeline** drop-down, select **XmlToJSON**, and then click **OK**.  
  
   5. Click **OK** until you exit all open dialog boxes.  
  
3. Finally, bind the logical ports you created as part of the orchestration to the physical ports you created now to configure the application.  
  
   1. Right-click **BizTalk Application 1**, and then click **Configure**.  
  
   2. From the left pane, click **ProcessPO**. From the right pane, associate a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host, map the logical ports to the physical ports, and then click **OK**.  
  
   3. Right-click **BizTalk Application 1**, and then click **Start**.  
  
## Test the application  
  
1.  Navigate to the sample you downloaded, and from the **TestMessage** folder, copy **JsonPurchaseOrder.json**, and paste it in the folder you associated with the receive location. Wait till the file disappears.  
  
2.  Navigate to the folder that you associated with the send port you created. Notice that a ***\<GUID\>*.json** file is available in the folder. Open the file and verify that it’s the invoice message.  
  
## See Also  
 [Processing JSON messages using BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)