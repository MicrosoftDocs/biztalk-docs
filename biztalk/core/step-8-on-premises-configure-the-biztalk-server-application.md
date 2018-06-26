---
title: "Step 8 (On Premises): Configure the BizTalk Server Application | Microsoft Docs"
ms.custom: ""
ms.date: "2015-12-08"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5109fb54-8453-444f-bc9c-070a65053397
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8 (On Premises): Configure the BizTalk Server Application
In the previous step you created a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration. In this step, you’ll build, deploy, and configure the application.  

## Build and deploy the application  

1.  In Visual Studio, right-click the solution name in the Solution Explorer, and click **Build**.  

2.  The deployment process requires that assembly is strongly signed.  You must sign your assemblies by associating the project with a strong name assembly key file.  

    1.  In Solution Explorer, right-click the **OrderProcessingDemo** project, and then click **Properties**.  

    2.  Click the **Signing** tab, and select the **Sign the assembly** checkbox.  

    3.  From the drop-down list in the **Choose a strong name key file** box, select **\<New…\>**.  

    4.  In the **Create Strong Name Key** dialog box, enter a name for the key file, for example `OrderProcessingDemo.snk`. Clear the checkbox for protecting the key file with a password, and then click **OK**.  

3.  Click the **Deployment** tab, in the box to the right of **Application Name**, type `OrderProcessingDemo`.  

4.  From the drop-down list in the box to the right of **Redeploy**, select **True**.  

5.  In Solution Explorer, right-click **OrderProcessingDemo**, and then click **Deploy**.  The Output window should display:  

    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  

    ```  

## Configure the application  

1. Click **Start**, point to **All Programs**, point to **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  

2. In the console tree on the left pane, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.  

3. Expand **BizTalk Group**, expand **Applications**, expand **OrderProcessingDemo**, and then click **Orchestrations**. You will see that the **OrderProcessingDemo.OrderProcessing** orchestration is deployed.  

4. In the orchestration, you created a logical port (**ReceiveSO**) to receive messages from the Service Bus Queue. In this step, you create a physical receive port to map to the logical port.  

   1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  

   2. On the **General** tab, do the following:  


      |                Use this                |     To do this      |
      |----------------------------------------|---------------------|
      |                **Name**                | Type **ReceiveSO**. |
      | **Enable routing for failed messages** |       (clear)       |


   3. Click **Receive Locations**, and then click **New**.  

   4. From Receive Location1 – Receive Location Properties dialog box, do the following:  


      |       Use this       |              To do this              |
      |----------------------|--------------------------------------|
      |       **Name**       |      Type **ReceiveOrders_SO**.      |
      |       **Type**       |       Select **SB-Messaging**.       |
      | **Receive handler**  | Select **BizTalkServerApplication**. |
      | **Receive pipeline** |        Select **XMLReceive**.        |


   5. Click **Configure**.  

   6. From SB-Messaging Transport Properties dialog box, on the **General** tab, for **Queue or Subscription URL**, enter **sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi**. Here, *mynamespace* is the Service Bus namespace and *queueordersedi* is the Service Bus Queue that you created in [Step 3 (For Azure): Create a Service Bus Queue](../core/step-3-for-azure-create-a-service-bus-queue.md).  

   7. From SB-Messaging Transport Properties dialog box, on the **Authentication** tab, specify the following values:  

      |Use this|To do this|  
      |--------------|----------------|  
      |**Access Control Service STS Uri**|Type `https://mynamespace-sb.accesscontrol.appfabriclabs.com/`|  
      |**Issuer name**|Specify the issuer name. Typically this is set to `owner`.|  
      |**Issuer key**|Specify the issuer key.|  

      > [!NOTE]
      >  You can get the values for the Queue URL, ACS URL, issuer name and key from the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886).  

   8. Click **OK** until you exit all the dialog boxes.  

5. In the orchestration, you created a logical port (**SendToSQL**) to send messages to the **SalesOrder** database table. In this step, you create a physical send port to map to the logical port.  

   1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

   2. On the General tab, do the following:  


      |     Use this      |              To do this              |
      |-------------------|--------------------------------------|
      |     **Name**      |         Type **SendToSQL**.          |
      |     **Type**      |         Select **WCF-SQL**.          |
      | **Send handler**  | Select **BizTAlkServerApplication**. |
      | **Send pipeline** |     Select **PassThruTransmit**.     |


   3. Click **Configure**.  

   4. From WCF-SQL Transport Properties, on the **General** tab, do the following:  


      |     Use this      |                                                                                                                                                                                    To do this                                                                                                                                                                                    |
      |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | **Address (URI)** | Type **mssql://computername/database_instance_name/databasename**. For example, to connect to a **DemoDB** database on the local computer running under the default database instance, enter `mssql://.//DemoDB`<br /><br /> For more information, see [Create the SQL Server connection URI](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md). |
      |    **Action**     |                                                                                                                                                                     Type **TableOp/Insert/dbo/SalesOrder**.                                                                                                                                                                      |


   5. From WCF-SQL Transport Properties, on the **Credentials** tab, select **Do not use Single Sign-On**, and specify credentials (case-sensitive) to connect to the SQL Server database you specified in the connection string. If you want to connect using Windows Authentication, leave the credentials blank.  

   6. Click **OK** until you exit all the dialog boxes.  

6. In the orchestration, you created a logical port (**SendToFile**) to send messages to a shared file location. In this step, you create a physical send port to map to the logical port.  

   1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **OrderProcessingDemo** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

   2. On the General tab, do the following:  


      |     Use this      |              To do this              |
      |-------------------|--------------------------------------|
      |     **Name**      |         Type **SendToFile**.         |
      |     **Type**      |           Select **File**.           |
      | **Send handler**  | Select **BizTAlkServerApplication**. |
      | **Send pipeline** |       Select **XML Transmit**.       |


   3. Click **Configure**.  

   4. From File Transport Properties, do the following:  


      |      Use this      |                        To do this                        |
      |--------------------|----------------------------------------------------------|
      | **Receive folder** | Specify the location where you want to send the message. |
      |   **File name**    |               Retain **%MessageID%.xml**.                |


   5. Click **OK** until you exit all the dialog boxes.  

7. You must now bind the physical and logical ports together to configure the application.  

   1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Configure**.  

   2. From Configure Application, in the left pane, click **OrderProcessing**.  

   3. Use the values in the following table to configure the application.  


      |            Use this             |             To do this              |
      |---------------------------------|-------------------------------------|
      |          For **Host**           | Select **BizTalkServerApplication** |
      | For logical port **ReceiveSO**  | Select physical port **ReceiveSO**  |
      | For logical port **SendToSQL**  | Select physical port **SendToSQL**  |
      | For logical port **SendToFile** | Select physical port **SendToFile** |


   4. Click **OK** to save the configuration.  

## Start the application  

1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **OrderProcessingDemo**, and then click **Start**.  

2. From the dialog, click **Start**.  

## See Also  
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)