---
title: "BPEL Import (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BPEL, orchestrations"
  - "examples, orchestrations"
  - "examples, BPEL Import Wizard"
  - "BPEL, examples"
  - "BPEL Import Wizard, examples"
  - "BPEL Import Wizard, orchestrations"
ms.assetid: 3fc70608-ccd9-4249-b238-c09fc6551db1
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BPEL Import (BizTalk Server Sample)
The BPEL Import sample demonstrates how to create an orchestration from a Business Process Execution Language (BPEL) process description and its related artifacts.  

## What This Sample Does  
 Wide World Importers is a shipping company that provides automated shipping services to retailers. Specifically, Wide World Importers enables retailers to:  

- Request order shipments  

- Track shipments  

- Confirm shipments  

- Confirm invoicing and payment for shipments  

  While the availability of these services can be represented by using a Web Services Description Language (WSDL) document, a BPEL document describes the typical way in which the product companies are expected to call the services and how to expect responses from Wide World Importers.  

  When Northwind Traders hires Wide World Importers to handle their shipping, they are provided a BPEL file and some related artifacts that describe the entire interaction. Using the BPEL file, Northwind Traders creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application (BPELShipping) to automatically process orders through Wide World Importers.  

  This sample walks you through this scenario in which the BPELShipping application:  

1. Receives an order from the Northwind Traders customer order system.  

2. Sends a shipping request to Wide World Importers and requests confirmation.  

3. Receives shipment request confirmation from Wide World Importers.  

4. Receives pickup notification from Wide World Importers.  

5. Receives shipment status messages up to and including when the shipment has been received by the customer.  

6. Receives an invoice from Wide World Importers.  

7. Responds to Wide World Importers with an invoice acknowledgment.  

8. Receives a payment confirmation from Wide World Importers.  

9. Sends a final shipping confirmation to the ordering system.  

   A separate BizTalk application (ShipperProcess) is used to simulate Wide World Importers for this sample. The BPELShipping application communicates with ShipperProcess by using the FILE transport, which uses common file system locations for the communication.  

## How This Sample is Designed and Why  
 BPEL for Web services is an XML-based language to describe the business process so that it can be easily shared across different companies who want to do business with each other using Web services. BPEL describes how to handle the business process at the business protocol level, but it does not describe the internal process in a company, such as the steps a company would take to process a purchase order after receiving it from a partner. This sample is designed to show you how to import BPEL and corresponding WSDL files, convert them into an orchestration, and then start to run the business process with the partner.  

 The following is the step-by-step procedure showing how to import the BPEL and WSDL files and convert them into an orchestration to interact with a prebuilt BizTalk application (ShipperProcess). If you complete the following steps, you do not need to perform the steps described in "To build and initialize the BPELShipping application".  

#### To import from BPEL and build a working solution  

1. In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, click **New**, and then click **Project**.  

   > [!NOTE]
   >  Before completing this procedure, you must set up the ShipperProcess application to create the supporting processes and schema projects.  

2. In the **New Project** dialog box, in the Project Types pane, select **BizTalk (Projects)**. In the Templates pane, select **BizTalk (Server) BPEL Import Project**.  

3. In the **Name** box, enter **BPELShipping**.  

   > [!NOTE]
   >  If you use a different name, you may experience problems with the final binding step.  

4. Select a location for the project, and then click **OK** to start the BPEL Import Wizard.  

5. On the **Welcome** page, click **Next**.  

6. On the **Select BPEL, WSDL, and XSD Files** page, click **Browse**.  

7. Select all the files from the \<*Samples Path*\>\Orchestrations\BPELImport\BPELSource folder, click **Open**, and then click **Next**.  

   > [!NOTE]
   >  In this step, you select the BPEL and WSDL files to describe the business process and the XSD files to represent the business document schemas.  

8. On the **Select WSDL Files for Invoked WebServices** page, click **Finish**.  

9. After the BPEL Import Wizard reports a successful import, close the wizard. The project is now created.  

10. At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the project location.  

11. Run the following command:  

     **sn –k BPELShipping.snk**  

12. In Solution Explorer, right-click the **BPELShipping** project, and then click **Properties**.  

13. Under **Common Properties\Assembly**, select the assembly key file **BPELShipping.snk** created in step 11, and then click **OK**.  

14. In Solution Explorer, select all the .xsd files and delete them.  

15. In Solution Explorer, select **Add Reference**, and on the **Projects** tab, click **Browse**.  

16. Select **ShippingSchemas.dll** from the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development, and then click **OK**.  

    > [!NOTE]
    >  The section "To build and initialize the ShipperProcess application" has instructions on how to build this.  

17. In Solution Explorer, double-click **OrderShippingProcess.bpel.odx**.  

18. On the **View** menu, select **Other Windows/Orchestration View**.  

19. In the Orchestration View window, right-click **Orchestration Properties** and then click **Properties Window**.  

20. In the Properties window, set the **Orchestration Exportable** property to **False**.  

21. In Solution Explorer, double-click **OrderShipping.wsdl.odx**.  

22. In the Orchestration View window, expand **Types/Multipart Message Types**.  

23. Expand **InvoiceAckMessageType** and then click **InvoiceAckMessagePart**.  

24. In the Properties window, expand the **Type** field, and select **Schemas/Select from referenced Assembly**.  

25. In the **Select Artifact Type** dialog box, click **ShippingSchemas**, select the **Imported_InvoiceAckMessage** type, and then click **OK**.  

    > [!NOTE]
    >  In steps 23 through 25, you replace the message type of the services that participate in the BPEL process to the corresponding message types described in the ShippingSchemas.  

26. Repeat steps 23 through 25 for each message type using the following values.  


    |          Message part          |                    Message type                     |
    |--------------------------------|-----------------------------------------------------|
    |       InvoiceMessagePart       |       ShippingSchemas.Imported_InvoiceMessage       |
    |      OrderAckMessagePart       |      ShippingSchemas.Imported_OrderAckMessage       |
    |        OrderMessagePart        |        ShippingSchemas.Imported_OrderMessage        |
    | PaymentConfirmationMessagePart | ShippingSchemas.Imported_PaymentConfirmationMessage |
    | PickupNotificationMessagePart  | ShippingSchemas.Imported_PickupNotificationMessage  |
    |  ShipConfirmationMessagePart   |  ShippingSchemas.Imported_ShipConfirmationMessage   |
    |      ShippingHistoryPart       |      ShippingSchemas.Imported_ShippingHistory       |
    |   ShipRequestAckMessagePart    |   ShippingSchemas.Imported_ShipRequestAckMessage    |
    |     ShipRequestMessagePart     |     ShippingSchemas.Imported_ShipRequestMessage     |
    |     ShipStatusMessagePart      |     ShippingSchemas.Imported_ShipStatusMessage      |


27. In Solution Explorer, right-click the **BPELShipping** project, point to **Add**, and then click **Existing Item**.  

28. Select all the .btm files from the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping.  

29. In the Orchestration View window, locate the **Message Assignment** shape named MessageAssignment_1 in ConstructMessage1 and delete it.  

30. From the Toolbox, drag a **Transform** shape into the ConstructMessage1 shape.  

31. In the Properties window, click the ellipsis button (**…**) and open the **Transform Configuration** dialog box.  

32. Select **Existing Map**.  

33. Select the fully qualified map name as **BPELShipping.Order2ShipRequest**.  

34. Select the source as **order.OrderMessagePart**.  

35. Select the destination as **ship_request.ShipRequestMessagePart** and click **OK**.  

36. Repeat steps 29 through 35 for each of the **Message Assignment** shapes and replace them with **Transform** shapes according to the following table.  


    |  Shape to replace   |              Map to use              |      Source document       |       Destination document        |
    |---------------------|--------------------------------------|----------------------------|-----------------------------------|
    | MessageAssignment_2 |     BPELShipping.Order2OrderAck      |   order.OrderMessagePart   |   order_ack.OrderAckMessagePart   |
    | MessageAssignment_3 |     BPELShipping.Order2OrderNAck     |   order.OrderMessagePart   |   order_ack.OrderAckMessagePart   |
    | MessageAssignment_4 |    BPELShipping.Order2ShipHistory    |   order.OrderMessagePart   | ship_history.ShippingHistoryPart  |
    | MessageAssignment_5 |  BPELShipping.ShipHistory2Completed  |   order.OrderMessagePart   | ship_history.ShippingHistoryPart  |
    | MessageAssignment_6 |       BPELShipping.Invoice2Ack       | invoice.InvoiceMessagePart | invoice_ack.InvoiceAckMessagePart |
    | MessageAssignment_7 | BPELShipping.Order2FinalConfirmation |   order.OrderMessagePart   | order_shipped.OrderAckMessagePart |


37. Save the orchestration.  

38. Double-click **Rule_1** in the **Decide** shape **Decision_1**.  

39. In BizTalk Expression Editor, replace  

     ship_request_ack(BPELShipping.Ship_Acknowledged) == true  

     with  

     ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true  

40. Double-click the **Loop** shape named **Loop_1**.  

41. In BizTalk Expression Editor, replace  

     ship_history(BPELShipping.Ship_Completed) == true  

     with  

     ship_history(ShippingSchemas.Ship_Completed) == true  

42. Double-click **Rule_2** in the **Decide** shape **Decision_2**.  

43. In BizTalk Expression Editor, replace  

     ship_status(BPELShipping.ShipStatus) == "DONE"  

     with  

     ship_status(ShippingSchemas.ShipStatus) == "DONE"  

44. In the Orchestration View, expand **Types/Correlation Types** and click ***OrderCorrelationSet_Type\\***.  

45. In the Properties window, click the ellipsis button (**…**) on **Correlation Properties**.  

46. In the Properties to correlate on pane, click **BPELShipping.OrderID**, and then click **Remove**.  

47. In the Available Properties pane, expand **Shipping Schemas**, select **Order ID**, and then click **Add**.  

48. Click **OK**.  

49. Save all the files and build the solution.  

50. Deploy the solution.  

51. Browse to the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\BPELShipping and double-click **BindAndStartOnly.bat** to bind and start the orchestration.  

## Where to Find This Sample  
 *\<Samples Path\>*\Orchestrations\BPELImport  

 The following table shows the files in this sample and describes their purpose.  

|File(s)|Description|  
|---------------|-----------------|  
|BPELSource\InvoiceAckMessage.xsd|Invoice acknowledgment schema.|  
|BPELSource\InvoiceMessage.xsd|Invoice schema.|  
|BPELSource\OrderAckMessage.xsd|Order acknowledgment schema.|  
|BPELSource\OrderHeader.xsd|Order header schema.|  
|BPELSource\OrderMessage.xsd|Order message schema.|  
|BPELSource\OrderShipping.wsdl|WSDL file referred to by BPEL.|  
|BPELSource\OrderShippingProcess.bpel|BPEL process flow.|  
|BPELSource\PaymentConfirmationMessage.xsd|Payment confirmation message.|  
|BPELSource\PickupNotificationMessage.xsd|Pickup notification message.|  
|BPELSource\ShipConfirmationMessage.xsd|Shipment confirmation message.|  
|BPELSource\ShippingHistory.xsd|Shipping history document.|  
|BPELSource\ShipRequestAckMessage.xsd|Ship request acknowledgment.|  
|BPELSource\ShipRequestMessage.xsd|Ship request message.|  
|BPELSource\ShipStatusMessage.xsd|Ship status message.|  
|Solution\bindings\BPELBindings.xml|Binding file specifying port bindings for the BPELShipping orchestration.|  
|Solution\bindings\ShipperBindings.xml|Binding file specifying port bindings for the ShipperProcess orchestration.|  
|Solution\BPELShipping\BindAndStartOnly.bat|Batch file to use for binding and starting the BPELImport orchestration after it has been built manually and deployed.|  
|Solution\BPELShipping\cleanup.bat|Batch file to use to remove the BPELShipping process.|  
|Solution\BPELShipping\Setup.bat|Batch file to use to install and start the provided BPELShipping sample.|  
|Solution\BPELShipping\BPELShipping.sln|The prebuilt BPELShipping sample.|  
olution\BPELShipping\BPELShipping\Invoice2Ack.btm|Invoice to invoice acknowledgment map.|  
|Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm|Map to convert from Order message to final shipment confirmation.|  
|Solution\BPELShipping\BPELShipping\Order2OrderAck.btm|Map to convert from Order message to order acknowledgment.|  
|Solution\BPELShipping\BPELShipping\Order2OrderNack.btm|Map to convert from Order message to order negative acknowledgment.|  
|Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm|Map to convert from Order message to Shipping history document.|  
|Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm|Map to convert from Order message to order Shipping request.|  
|Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm|Map to set the Shipping history to completed.|  
|Solution\ShipperProcess\setup.bat|Batch file to build, deploy, bind, and start the ShipperProcess helper orchestration and its ports.|  
|Solution\ShipperProcess\cleanup.bat|Batch file to stop, unenlist, and undeploy the ShipperProcess helper orchestration and its ports.|  

## Building and Initializing This Sample  
 The first step is to build and initialize the ShipperProcess application used to simulate Wide World Importers.  

#### To build and initialize the ShipperProcess application  

1. Start **Visual Studio Command Prompt**.  

2. From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:  

    *\<Samples Path\>*\Orchestrations\BPELImport\Solution\ShipperProcess  

3. Run the file Setup.bat, which performs the following actions:  

   -   Builds the ShippingSchemas project, which contains the schemas used in the ShipperProcess and the BPELShipping process  

   -   Builds the ShipperProcess  

   -   Deploys the ShippingSchemas and ShipperProcess projects  

   -   Creates and binds the send and receive ports used by ShipperProcess  

   -   Starts the ports used by ShipperProcess  

   -   Enlists and starts the ShipperProcess orchestration  

   You should confirm that no errors were reported during the build and initialization process before attempting to run this sample. One or more of the following warnings may be displayed; you can ignore these.  

```  
The 'http://contoso.org/samples/Fragments:XXXX' element is not declared. An error occurred at , (35, 16).  
<SAMPLE_LOCATION>\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(667,22): convoy found at 'activate receive(Receive_ShipOrder.Operation_1, Request, initialize Correl)'  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): and 'receive(ReceiveInvoiceAck.Operation_1, Invoice_Ack, Correl)'  
```  

> [!NOTE]
>  You do not need to perform the following steps if you completed the steps described in "To import from BPEL and build a working solution."  

#### To build and initialize the BPELShipping application  

1. > [!WARNING]
   >  Before executing these steps, you must complete the steps above entitled “To build and initialize the ShipperProcess application”.  

    From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:  

    *\<Samples Path\>*\Orchestrations\BPELImport\Solution\BPELShipping  

2. Run the file Setup.bat, which performs the following actions:  

   -   Builds the BPELShipping project  

   -   Deploys the BPELShipping project  

   -   Creates and binds the send and receive ports used by the BPELShipping process  

   -   Starts the ports used by the BPELShipping process  

   -   Enlists and starts the BPELShipping orchestration  

## Running This Sample  

#### To run the BPEL Import sample  

1.  Copy the **Order.xml** file from the *\<Samples Path\>*\Orchestrations\BPELImport\Solution folder to the \<*Samples Path\>*\Orchestrations\BPELImport\Solution\Ports\ReceiveOrder folder.  

2.  The BPELShipping orchestration picks up this file as an order from the customer order processing system, runs through the shipping process, and produces one file each in the \<*Samples Path*\>\Orchestrations\BPELImport\Solution\Ports\SendOrder folder and the \<*Samples Path*\>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation folder. The format of the name of these files is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.  

## Uninstalling This Sample  

#### To uninstall the BPEL Import sample  

1. At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*\>\Orchestrations\BPELImport\BPELShipping.  

2. Run Cleanup.bat.  

3. Browse to \<*Samples Path*\>\Orchestrations\BPELImport\ShipperProcess.  

4. Run Cleanup.bat.  

## See Also  
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)