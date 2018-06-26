---
title: "Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a9de95f-7d2c-437d-be5b-0062592f32c6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013
This section provides a step-by-step walkthrough on how to create a hybrid application involving [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## Business Scenario  
 Northwind is an enterprise that receives sales orders from its partners, one of them being Contoso, in the form of a flat-file EDI message. Northwind wants to set up an end-to-end application that does the following:  

- **Manage the EDI message processing** – This module of the application must verify that the message received from Contoso conforms to the standard EDI message formats. This module must also generate all the required acknowledgements to verify that the message is successfully processed.  

- **Use business logic to process the data** – Once the EDI message is successfully verified and processed, Northwind must run the message against business logic for further processing. For example, if the order quantity in the received message is more than a given amount, the data is stored in a SQL Server database. Otherwise, the data is sent to a shared file location.  

  To achieve this scenario, Northwind decides to set up a hybrid application where the EDI message processing is done on the cloud while the business-logic-driven data processing is done within the premises. To set up this hybrid application Northwind uses the following:  

- **[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]**  – The Azure BizTalk Portal available with [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] enables customers to configure trading partners and EDI agreements on [!INCLUDE[winazure](../includes/winazure-md.md)]. Northwind uses the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] – April 2012 release to create and deploy an agreement that processes the incoming EDI message, validates it against the X12 840 sales order schema, transforms the message to a schema required by Northwind, and then sends the message to a Service Bus Queue. So, to develop a hybrid application, the data should be sent from the Service Bus Queue to an on-premises application.  

- **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  – The new adapter for Service Bus (**SB-Messaging**) available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables applications to receive messages from Service Bus entities like Queues, Topics, and so on into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. As part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, Northwind uses an orchestration to decide whether the quantity requested in the received sales order is more than 100. If the quantity is more than 100, the message is inserted into a SQL Server database table called **SalesOrder**. If the quantity is less than 100, the message is sent to a shared file location.  

   To insert the message into a SQL Server database table, Northwind uses the [!INCLUDE[adaptersql](../includes/adaptersql-md.md)] available as part of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

### End-to-end Message Flow  
 This is how the message flows through the hybrid application:  

1. Contoso sends an X12 sales order message to the endpoint where the EDI agreement is deployed on the cloud.  

2. After the message is successfully processed through the EDI agreement, it is sent to the Service Bus Queue.  

3. SB-Messaging receive adapter consumes the message from the Service Bus Queue and instantiates the orchestration deployed in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send the message to different destinations based on the order quantity.  

4. If the quantity ordered is greater than 100, the orchestration inserts the message to a **SalesOrder** table. If the quantity ordered is less than or equal to 100, the message is written to a shared file location.  

## Set up Your Computer  
 This tutorial requires you to perform four broad activities. The following table lists the activities and the software requirements for each activity:  


|                                                            Activity                                                             |                                                                                                                                              Required software                                                                                                                                               |
|---------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                     Create the EDI artifacts required for the EDI agreement                                     | This tutorial was created with the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] – April 2012 release as well as the X12 840 sales order schema. These can be downloaded from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057). |
|                                               Create and deploy the EDI agreement                                               |                                                                                 Because the EDI agreement is deployed on Azure, you only need a Web browser (e.g. Internet Explorer) to log in to the Azure BizTalk Portal.                                                                                  |
| Build, deploy, and configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application |              If you want to provision a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer on an Azure VM, follow the instructions at [http://msdn.microsoft.com/library/azure/jj248689.aspx](http://msdn.microsoft.com/library/azure/jj248689.aspx).               |
|                                        Send a test message to the EDI agreement endpoint                                        |   You can use the MessageSender tool available in the samples package shipped with [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. You can download the samples package from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).   |

 You can opt to install all these on the same computer or on different computers.  

## In This Section  

-   [Step 1 (For Azure): Create the EDI Project](../core/step-1-for-azure-create-the-edi-project.md)  

-   [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md)  

-   [Step 3 (For Azure): Create a Service Bus Queue](../core/step-3-for-azure-create-a-service-bus-queue.md)  

-   [Step 4 (On Premises): Create the SQL Server Table](../core/step-4-on-premises-create-the-sql-server-table.md)  

-   [Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)  

-   [Step 6 (On Premises): Create a Transform to Map the Message from the Queue to the Insert Schema](../core/step-6-map-the-message-from-the-queue-to-the-insert-schema.md)  

-   [Step 7 (On Premises): Create an Orchestration](../core/step-7-on-premises-create-an-orchestration.md)  

-   [Step 8 (On Premises): Configure the BizTalk Server Application](../core/step-8-on-premises-configure-the-biztalk-server-application.md)  

-   [Step 9: Test the Solution](../core/step-9-test-the-solution.md)