---
title: "How to Run the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, validating"
  - "process management solution tutorial, submitting orders"
  - "process management solution tutorial, stopping orders"
  - "process management solution tutorial, updating orders"
ms.assetid: cb77651e-e16c-49dc-9f8a-88584cd68a8b
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Run the Business Process Management Solution
The following steps describe how to run and validate the Business Process Management solution on a single computer.  
  
-   [Start the Business Process Management Solution](#step1)  
  
-   [Run and validate the Business Process Management Solution](#step3)  
  
## Prerequisites  
 Before running the BPM solution, you must perform the steps in [How to Install the Business Process Management Solution](../core/how-to-install-the-business-process-management-solution.md).  
  
##  <a name="step1"></a> Start the Business Process Management Solution  
  
#### To start the Business Process Management Solution  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**.  
  
3. In the **BizTalk Server Administration Console**, expand **BizTalk Group**, and then expand **Applications**.  
  
   1.  Right-click BTSScn.BPM.MessagingApp, click **Start**, and then click **Start** on the **Start Application** dialog box.  
  
   2.  Right-click BTSScn.BPM.OrderBrokerApp, click **Start**, and then click **Start** on the **Start Application** dialog box.  
  
   3.  Right-click BTSScn.BPM.CableOrderApp, click **Start**, and then click **Start** on the **Start Application** dialog box.  
  
   4.  Right-click BTSScn.BPM.OrderBrokerApp.Test, and click **Stop**. In the **Stop Application** dialog box, select **Full Stop - Terminate instance**, and then click **Stop**.  
  
   > [!NOTE]
   >  To insert information in the history database. the OrderBroker orchestration uses the HistoryPort send port of which the **Delivery Notification** property is set **Transmitted**. The send port is bounded to the HistoryInsert-SPG send group which includes the HistoryInsert-SP and HistoryInsert-Test-SP send ports. For these two send ports the message engine will publish two acknowledgment messages to the OrderBroker orchestration. It makes the orchestration suspended due to unconsumed messages. To avoid this situation, you must unenlist one of the send ports. In this walkthrough, unenlist HistoryInsert-Test-SP send port by fully stopping the BTSScn.BPM.OrderBrokerApp.Test application. For more information about the OrderBroker orchestration, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md). For more information about **Delivery Notification** property, see [Using Acknowledgments](../core/using-acknowledgments.md).  
  
4. Run the Facilities Simulator as follows:  
  
   1.  Open a command prompt, change the directory to the %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug folder.  
  
   2.  Type `BTSScnBPMFacilities.exe`, and then press ENTER. Keep the FacilitiesSimulator running. This application simulates the facilities processing back-end systems at Southridge Video.  
  
   3.  In the FacilitiesSimulator, type the following receive and transmit queues:  
  
       |Name|Value|  
       |----------|-----------|  
       |**Receive Queue**|`.\private$\ToFacilitiesQ`|  
       |**Transmit Queue**|`.\private$\FromFacilitiesQ`|  
  
   4.  In the FacilitiesSimulator, Click **Start**.  
  
5. Run the Operation Server as follows:  
  
   1.  Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\OperationsServer\bin\debug folder.  
  
   2.  Type `BTSScnBPMOperations.exe 8881` at the command prompt, and then press ENTER. Keep the Operation Server running. The Operation Server listens on the TCP port, 8881, to receive error messages from the Ops Adapter. It displays the error messages received by the Ops Adapter.  
  
6. Run the Cable Provisioning System as follows:  
  
   1.  Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug folder.  
  
   2.  Type `BTSScnBPMProvisioning.exe 8880`, and then press ENTER. Then, keep the Cable Provisioning System running. The Cable Provisioning System listens on the TCP port, 8880. This application simulates a back-end order system, and displays the final orders.  
  
##  <a name="step3"></a> Run and validate the Business Process Management Solution  
  
#### To submit a new order and validate the solution  
  
1.  In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order.**  
  
    |Entry|Value|  
    |-----------|-----------|  
    |Customer ID|1|  
    |Order ID|1|  
    |Sequence Number|1|  
    |Service Type Code|New Standard Service|  
  
3.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 1 Order ID 1 Sequence Number 1**  
  
4.  Validate that the placed order at the command prompt running the Cable Provisioning System. The application display the messages that the submitted order is analyzed, activated, and then completed.  
  
5.  Validate that the number of the total messages is incremented by one on the Facilities Simulator.  
  
#### To submit a duplicate while the BizTalk Server is processing the original order  
  
1.  In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  In the FacilitiesSimulator, click **Stop**. It prevents submitted orders from being processed further.  
  
3.  On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order** twice to simulate duplicated orders.  
  
    |Entry|Value|  
    |-----------|-----------|  
    |Customer ID|2|  
    |Order ID|1|  
    |Sequence Number|1|  
    |Service Type Code|New Standard Service|  
  
4.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 2 Order ID 1 Sequence Number 1**  
  
5.  In the FacilitiesSimulator, click **Start**. The orchestrations waiting for the responses from the Facilities Simulator will resume. It simulates that a duplicate order is submitted while the first order is being processed.  
  
6.  Check the placed orders at the command prompt running the Cable Provisioning System. The application displays the messages that only the first order is analyzed, activated, and then completed.  
  
7.  Check the error message for the duplicated orders at the command prompt running the Operation Server.  
  
#### To update an order while the BizTalk Server is processing the order  
  
1.  In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  In the FacilitiesSimulator, click **Stop**.  
  
3.  On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.  
  
    |Entry|Value|  
    |-----------|-----------|  
    |Customer ID|3|  
    |Order ID|1|  
    |Sequence Number|1|  
    |Service Type Code|New Standard Service|  
  
4.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 3 Order ID 1 Sequence Number 1**  
  
5.  On the **Southridge Video Customer Service Rep Order Entry Form** page, enter an updated order in the following table, and then click **Submit Order**.  
  
    |Entry|Value|  
    |-----------|-----------|  
    |Customer ID|3|  
    |Order ID|1|  
    |Sequence Number|2|  
    |Service Type Code|New Deluxe Service|  
  
6.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 3 Order ID 1 Sequence Number 2**  
  
7.  In the FacilitiesSimulator, click **Start**  
  
8.  Check the result message on the **Southridge Video Customer Service Rep Order Entry Form** page.  
  
9. Check the placed orders at the command prompt running the Cable Provisioning System. The application displays the messages that two orders are analyzed, but only the updated order is activated and completed.  
  
10. Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the original order was interrupted.  
  
11. Checked the routing failure error message at the command prompt running the Operation Server.  
  
    > [!NOTE]
    >  There will be an error in the event log and in the operations server. The response message from the Facilities System no longer correlates back to an instance of the business process as it was terminated by the interruption caused by the new order with a higher sequence number. Therefore response message is orphaned and will get routed to the operations server. For more information about order updates, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).  
  
12. Open the latest message in the %SystemDrive%:\BPMTest\HistoryUpdate-SP folder with Notepad. Check **CustName**, **OrderNum**, **OrderSeqNum**, and **Status** fields to see if the message has been created for the new order and the **Status** field is **COMPLETED**.  
  
#### To terminate an order while the BizTalk Server is processing the order  
  
1.  In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  In the FacilitiesSimulator, click **Stop**.  
  
3.  On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.  
  
    |Entry|Value|  
    |-----------|-----------|  
    |Customer ID|4|  
    |Order ID|1|  
    |Sequence Number|1|  
    |Service Type Code|New Standard Service|  
  
4.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 4 Order ID 1 Sequence Number 1**  
  
5.  On the **Southridge Video Customer Service Rep Order Entry Form** page, click **Terminate Order**.  
  
6.  On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:  
  
     **Customer ID 4 Order ID 1 Sequence Number 1**  
  
7.  In the FacilitiesSimulator, click **Start**.  
  
8.  Check the placed orders at the command prompt running the Cable Provisioning System. The application displays the messages that order is only analyzed and activated.  
  
9. Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the order was terminated by user.  
  
    > [!NOTE]
    >  For more information about terminating orders, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).  
  
10. Checked the routing failure error message at the command prompt running the Operation Server.  
  
## See Also  
 [Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md)   
 [Developer Machine Setup for the Business Process Management Solution](../core/developer-machine-setup-for-the-business-process-management-solution.md)