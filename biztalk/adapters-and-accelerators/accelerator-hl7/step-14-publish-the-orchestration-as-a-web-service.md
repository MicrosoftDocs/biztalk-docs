---
title: "Step 14: Publish the Orchestration as a Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, publishing"
  - "publishing, orchestrations"
  - "Web services, orchestrations"
  - "message enrichment tutorial, orchestrations"
  - "publishing, Web services"
  - "message enrichment tutorial, Web services"
ms.assetid: 8f29a7be-a679-4ca6-a648-35338d9e9e98
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 14: Publish the Orchestration as a Web Service
In this step, you use the BizTalk Web Services Publishing Wizard to publish your orchestration as a Web service.  
  
 Before publishing the orchestration as a Web service, you need to ensure that the logon account for BizTalkServerIsolatedHost is part of the BizTalk Isolated Host Users group, so it has access to the BizTalk databases. This is necessary because the receive handler for the SOAPReceivePort receive location that is created by the Web Service Publishing Wizard for this tutorial is BizTalkServerIsolatedHost, not BizTalkServerApplication. The receive handler is BizTalkServerIsolatedHost because the SOAP adapter runs under the IIS process, not the BizTalk process.  
  
### To ensure access privileges for the SOAPReceivePort receive location  
  
1.  In BizTalk Server Administration Console, under **Host Instances** in the **Platform Settings** node, right-click **BizTalkServerIsolatedHost**, and then click **Properties**. In the Properties dialog box, click **Configure**. Note the **Logon** account.  
  
2.  In the Computer Management dialog box, under **Groups** in the **Local Users and Groups** node, double-click **BizTalk Isolated Host Users**. If the logon account for **BizTalkServerIsolatedHost** is not a member of **BizTalkServerIsolatedHost**, add it to the group.  
  
### To run the BizTalk Web Services Publishing Wizard  
  
1. In Solution Explorer of Visual Studio, click **Solution 'BTAHL7V22Common'**. On the **Tools** menu, click **BizTalk Web Services Publishing Wizard**.  
  
2. In the **BizTalk Web Services Publishing Wizard**, on the **Welcome** page, click **Next**.  
  
3. On the **Create Web Service** page, select **Publish BizTalk orchestrations as web services**, and then click **Next**.  
  
4. On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** field, browse to or type **\<*drive*\>:\Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**, click **BTAHL7 Project.dll**, click **Open**, and then click **Next**.  
  
5. On the **Orchestrations and Ports** page, ensure that all nodes are selected, and then click **Next**.  
  
6. On the **Web Service Properties** page, for **Target namespace of web service**, type **http://localhost**, and then click **Next**.  
  
7. On the **Web Service Project** page, select **Allow anonymous access to web service** and **Create BizTalk receive locations in the following application**. Select **BizTalk Application 1** for the application. Keep the default in the **Location** field. Click **Next** to accept the default project location.  
  
8. On the **Web Service Project Summary** page, click **Create** to generate the ASP.NET Web Service project.  
  
9. Click **Finish** to close the wizard.  
  
10. Open the BizTalk Server Administration Console. In the console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  
  
11. Click **Receive Locations**, right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Properties**.  
  
12. In the Receive Location Properties dialog box, click **Receive Pipeline**, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive** from the drop-down list, and then click **OK**.  
  
13. Right-click **WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, and then click **Enable**.  
  
    Proceed to [Step 15: Configure the Send and Receive Ports](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md).  
  
## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)