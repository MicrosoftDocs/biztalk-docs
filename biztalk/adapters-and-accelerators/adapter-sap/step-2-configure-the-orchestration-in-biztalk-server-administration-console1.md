---
title: "Step 2: Configure the Orchestration in BizTalk Server Administration Console1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestration, configruing in BizTalk Server Administration console"
  - "WCF-Custom port, creating"
  - "migration"
ms.assetid: fb057bce-5702-4ea0-8ed5-e299d3a78a11
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Configure the Orchestration in BizTalk Server Administration Console
![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Time to complete:** 10 minutes  
  
 **Objective:** In this step, you perform the following tasks:  
  
- Create a WCF-Custom send-receive port to send and receive messages from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Configure this port to use the maps that you created in the previous step.  
  
- Configure the orchestration you deployed in the last step to use the WCF-Custom port.  
  
## Prerequisite  
  
-   Deploy the BizTalk orchestration for which you want to configure the WCF-Custom port.  
  
### To create a WCF-Custom port  
  
1. When you generate schema for an RFC using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], a binding file is also added to the BizTalk project. You can import this binding file into your BizTalk application to create a WCF-Custom send-receive port. For instructions on importing a binding file, see [Importing Bindings](http://msdn.microsoft.com/library/c927efde-29bd-4efe-9da5-942e7da65dbf).  
  
2. After you import the binding file, a send port is created under the **Send Ports** folder in the BizTalk Server Administration console.  
  
3. Right-click the WCF-Custom port, and then click **Properties**.  
  
4. From the left pane of the send port properties dialog box, click the **General** tab. From the right pane, click **Configure**.  
  
5. In the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and specify the credentials to connect to an SAP system.  
  
6. Click **OK**.  
  
7. From the left pane of the send port properties dialog box, click **Inbound Maps**. From the right pane, click the field under the **Map** column, and from the drop-down, select **ResponseMap**.  
  
    ![Configure the inbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/10129a7d-211b-464b-b05a-b3ea72f46873.gif "10129a7d-211b-464b-b05a-b3ea72f46873")  
  
8. From the left pane of the send port properties dialog box, click **Outbound Maps.** From the right pane, click the field under the **Map** column, and from the drop-down, select **RequestMap**.  
  
    ![Configure the outbound map on the WCF custom port](../../adapters-and-accelerators/adapter-sap/media/4ffcb4cd-4f53-4b67-92e2-3225d15d97ee.gif "4ffcb4cd-4f53-4b67-92e2-3225d15d97ee")  
  
9. Click **OK**.  
  
### To configure the BizTalk application  
  
1. In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then expand the BizTalk Application where the orchestration is deployed.  
  
2. Right-click the BizTalk application, and then select **Configure**.  
  
3. From the left pane, click the orchestration to configure. From the right pane, from the **Host** drop-down list, select a BizTalk host instance.  
  
4. Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.  
  
   1. Select the file port where you will drop a request message. The BizTalk orchestration will consume the request message and send it to the SAP system.  
  
   2. Select the file port where the BizTalk orchestration will drop the response message containing the response from the SAP system.  
  
   3. Select the WCF-custom send port you created earlier in this topic.  
  
   4. Click **OK**.  
  
      For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).  
  
## Next Steps  
 You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends messages to the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. You must now test the migrated BizTalk application by sending a request message to invoke the SD_RFC_CUSTOMER_GET RFC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md).  
  
## See Also  
 [Tutorial 2: Migrating an SAP RFC BizTalk Project](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)