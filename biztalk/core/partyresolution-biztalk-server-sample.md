---
title: "PartyResolution (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "examples, parties"
  - "orchestrations, examples"
  - "parties, examples"
  - "parties, orchestrations"
  - "examples, routing"
  - "orchestrations, parties"
  - "examples, orchestrations"
  - "examples, messages"
  - "routing, messages"
  - "messages, routing"
ms.assetid: 220e6bc5-6f04-4f37-b0d0-f11c2cc14422
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PartyResolution (BizTalk Server Sample)
The PartyResolution sample demonstrates how to use BizTalk orchestrations with party resolution to route messages to one of two possible recipients.  

## What This Sample Does  
 This sample runs multiple orchestrations that demonstrate the following different roles:  

-   Buyer orchestration, used to initiate the purchase order (PO) message processing.  

-   Supplier orchestration, which demonstrates both inbound and outbound party resolution.  

-   ShipmentAgency1 and ShipmentAgency2 orchestrations, which respond to the supplier orchestration based on the shipment destination in the PO.  

## How This Sample is Designed and Why  
 Party resolution refers to the process of determining who (that is, what party) sends a message. For example, you may want to enable only known parties to send a message. Outbound party resolution is the process by which you determine which parties should be sent a message.  

 In addition to party resolution, this sample demonstrates how to implement and use roles. For example, to process the shipment of your product, you create a send port to which you send a document instructing a shipper to ship your product. If you have multiple shippers to choose from, you can create a shipper role in your orchestration rather than create multiple send ports whose only difference is the shipper's URL. You can then send messages relating to product shipment to the shipper role. You create parties and associate a send port to each party and party certificate. Finally, you enlist each party to the shipper role to enable it. In the orchestration, you can then dynamically specify which shipper you are sending the message to.  

 This sample also demonstrates how to use correlation to match the incoming message to the right orchestration instance.  

- The business process flows for the buyer, supplier, and shipping agencies are as follows:  

- Buyer business process flow:  

  1.  Receive PO message from internal department as an .xml file.  

  2.  Send PO message to supplier.  

- Supplier business process flow:  

  1.  Resolve the party (inbound party resolution) to update the source party based on signature certificate.  

  2.  Receive an activation message (PO) from buyer.  

  3.  Send a PO Acknowledgement message to buyer.  

  4.  Verify the delivery country/region.  

  5.  Resolve the outbound party to find which shipping agency to use. If the country/region is U.S., the shipping agency is ShipmentAgency2. If the country/region is Canada, the shipping agency is ShipmentAgency1.  

  6.  Send a Shipment Order Request message to the appropriate shipping agency.  

  7.  Receive the Shipment Order Acknowledgement message from the appropriate shipping agency.  

  8.  Send a Shipment Advice message to the appropriate shipping agency.  

  9. Receive a Shipment Advice Acknowledgement message from the appropriate shipping agency.  

  10. Send a final PO Delivery Receipt message to the buyer.  

- Shipping agency business process flow (same for both shipping agencies):  

  1.  Receive the Shipment Order Request message from the supplier.  

  2.  Generate and send an Acknowledgement message for the Shipment Order Request message.  

  3.  Receive a Shipment Advice message from the supplier.  

  4.  Generate and send an Acknowledgement message for the Shipment Advice message.  

  The following statements explain how this sample is designed:  

- The BuyerProcess.odx orchestration receives a message and uses the custom pipeline MimePartyResSendPipeline to encode the message and send it to the supplier. This is done by using Pipeline Designer to build and deploy a custom send pipeline. Before sending the message to the supplier, the message is digitally signed with buyer's private key, which is specified in BizTalk Group Properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.  

- The SupplierProcess.odx orchestration uses the custom pipeline MimePartyResReceivePipeline, which includes a MIME/SMIME decoder component, to decode the message and perform inbound party resolution by using the buyer's public key to resolve and validate the buyer's identity. This is done by building and deploying a custom receive pipeline.  

- The supplier orchestration then initiates the POCorrelationSets which is defined to base on a promoted property - PONo. The PONo is used to match the inbound and outbound messages to this orchestration instance in the later stage, because there are multiple send and receive actions throughout the entire orchestration.  

- The supplier orchestration implements role links to deal with inbound and outbound party resolution. The supplier orchestration uses two role link types:  

  -   Buyer_Supplier role link type  

  -   Supplier_Shipment role link type  

- In the Buyer_Supplier **Role Link** shape, the supplier is in the Provider role and the buyer is in the Consumer role because the supplier receives the first message from the buyer. When the supplier orchestration sends the acknowledgment to the buyer role, there is a send port associated with the buyer, and the message is sent to the buyer through the specified send port. To find the send port, right-click **BuyerAgency** in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and then click **Properties**. The send port is displayed under **Send Ports**.  

- The orchestration then uses the following expression to return the partner information, and writes an XML file to a folder through a call to an external assembly named CheckPartyName.  

  ```  
  Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty)  
  ```  

- In the Supplier_Shipment **Role Link** shape, the Shipment role contains a send port with two operations that are used to send the message from the supplier to the appropriate shipping agency depending on the destination party. The Supplier role contains a receive port with two operations that are used to receive the response from the shipping agency. The correlation is used when sending and receiving these messages, and it is based on the PONo.  

  > [!NOTE]
  >  When you bind the supplier orchestration, you will find that only one send port and two receive ports need to be bound. This is because the send ports to the destination parties are already bound with the parties. Moreover, one of the receive ports in the orchestration contains two receive operations, so even if you see three **Receive** shapes, only two of them need to be bound.  

- The supplier orchestration uses the first line in the following code to get the shipment agency by calling an external assembly named QueryShipmentCatalogComponent. It then uses the second line to set the destination party for the shipment role.  

  ```  
  strShipmentName= objQueryShipmentCatalog.GetShipmentDetails(POMessage.MessagePart_1.POHeader.Address.Country);  
  Supplier_Shipment(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party(strShipmentName,"OrganizationName");  
  ```  

- Shipper1Process.odx and Shipper2Process.odx are built to receive the shipping order and the shipping advice from SupplierProcess.odx and to send the response back to SupplierProcess.odx. In both of the shipper orchestrations, correlation is used, and the correlation type is based on the promoted property PONo.  

## Where to Find This Sample  
 *\<Samples Path\>*\Orchestrations\PartyResolution\  

 The following table shows the files in this sample and describes their purpose.  


|                                                                                                                                 File(s)                                                                                                                                 |                                                                                                                                                              Description                                                                                                                                                              |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                      BuyerBinding.xml, ShippingAgency1Binding.xml, ShippingAgency2Binding.xml, SupplierBinding.xml                                                                                      |                                                                                                                                            Used for automated setup such as port binding.                                                                                                                                             |
|                                                                                                                               Cleanup.bat                                                                                                                               |                                                                   Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.                                                                    |
|                                                                                                                           PartyResolution.sln                                                                                                                           |                                                                                                                              Solution file that contains all of the projects in the various subfolders.                                                                                                                               |
|                                                                                                                            PurchaseOrder.xml                                                                                                                            |                                                                                                                                                           Sample input PO.                                                                                                                                                            |
|                                                                                                                                Setup.bat                                                                                                                                |                                                                                                                                         Used to build and initialize portions of this sample.                                                                                                                                         |
|                                                                                                    In the \Buyer folder:<br /><br /> Buyer.btproj, BuyerProcess.odx                                                                                                     |                                                                                                                             BizTalk project and orchestration used to implement the buyer in this sample.                                                                                                                             |
|                                                                                                             In the \Catalog folder:<br /><br /> Catalog.xml                                                                                                             |                                                                                                                         Used to determine shipment agency based on shipping destination specified in the PO.                                                                                                                          |
|                                                                                      In the \CheckPartyName folder:<br /><br /> AssemblyInfo.cs, CheckPartyName.csproj, Class1.cs                                                                                       |                                                                                                  Microsoft Visual C# project and source files for the CheckPartyName application used to access the properties of the source party.                                                                                                   |
|                                                                In the \FilePolling folder:<br /><br /> App.ico, AssemblyInfo.cs, FilePolling.cs, FilePolling.csproj, FilePolling.resx, FilePolling.sln,                                                                 |                                                                 Visual C# solution, project, source, and associated files for the FilePolling application.<br /><br /> Use this application to keep informed about the progressing state of this automated scenario.                                                                  |
|                                                                            In the \Pipeline\projectschema folder:<br /><br /> MimePartyResReceivePipeline.btp, MimePartyResSendPipeline.btp                                                                             |                                                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline files used by the different roles in this sample.                                                                                             |
|                                                                In the \QueryShipmentCatalogComponent folder:<br /><br /> AssemblyInfo.cs, QueryShipmentCatalog.cs, QueryShipmentCatalogComponent.csproj                                                                 | Visual C# project and source files for the QueryShipmentCatalog component used to access the shipment catalog defined in the file Catalog.xml.<br /><br /> The QueryShipmentCatalog component determines which shipment agency the supplier will use. It uses data from Catalog.xml to determine the best shipper based on geography. |
| In the \Schemas folder:<br /><br /> PODeliveryReceipt.xsd, POPropertySchema.xsd, PurchaseOrder.xsd, PurchaseOrderAcknowledgement.xsd, Schemas.btproj, ShipmentAdvice.xsd, ShipmentAdviceAcknowledgement.xsd, ShipmentOrderAcknowledgement.xsd, ShipmentOrderRequest.xsd |                                                                                                                                           Schemas used by the various roles in this sample.                                                                                                                                           |
|                                                                  In the \ShipmentAgency1 folder:<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency1.btproj, ShipmentOrderAck.btm, Shipper1Process.odx                                                                   |                                                                                                                      BizTalk project, orchestration, and maps used to implement ShipmentAgency1 in this sample.                                                                                                                       |
|                                                                  In the \ShipmentAgency2 folder:<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency2.btproj, ShipmentOrderAck.btm, Shipper2Process.odx                                                                   |                                                                                                                      BizTalk project, orchestration, and maps used to implement ShipmentAgency2 in this sample.                                                                                                                       |
|                                     In the \Supplier folder:<br /><br /> PO_POAck.btm, PO_ShipmentOrderRequest.btm, ShipmentAdviceAck_PODeliveryReceipt.btm, ShipmentOrder_ShipmentAdvice.btm, Supplier.btproj, SupplierProcess.odx                                     |                                                                                                                        BizTalk project, orchestration, and maps used to implement the supplier in this sample.                                                                                                                        |

## Building and Initializing This Sample  

> [!NOTE]
>  Before you build and initialize this sample, you need to make sure that the default BizTalk In-Process Host is configured as Authentication Trusted. For more information, see [BizTalk Server Runtime Security Recommendations](../core/biztalk-server-runtime-security-recommendations.md).  

 The MIME pipeline component is not supported in a 64-bit host instance. The host associated with the send and receive handler for the file adapter must be configured as a 32-bit only host. For more information on this see [How to Modify Host Properties](../core/how-to-modify-host-properties.md). If you already have a 32-bit only host configured on the system, and want to use it, see [Configuring the File Adapter](../core/configure-the-file-adapter.md) for instructions on configuring the host(s) associated to the file adapter’s send and receive handler.  

 The certificate mentioned in this section must to be added to the Personal store of the Logon account configured for the default BizTalk In-Process host instance which will be signing messages.  

 By default the setup.bat file mentioned below will install the Party Resolution sample into the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. You can modify the setup.bat file to deploy the sample into a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application by opening the setup.bat file and replacing the section preceded by the statement `@ECHO Deploy Assemblies...` with the following:  

```  
@ECHO Deploy Assemblies...  

btstask AddApp -ApplicationName:PartyResolutionSample -Description:"Party Resolution Orchestration sample from the SDK"  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Schemas\bin\Release\Schemas.dll -Options:GacOnAdd  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Pipeline\projectschema\bin\Release\ProjectSchema.dll -Options:GacOnAdd   
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Buyer\bin\Release\Buyer.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%BuyerBindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency1\bin\Release\ShipmentAgency1.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency1BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency2\bin\Release\ShipmentAgency2.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency2BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Supplier\bin\Release\Supplier.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%SupplierBindingFileName%  
```  

#### To build and initialize the PartyResolution sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*>\Orchestrations\PartyResolution  

2. Run the file Setup.bat, which performs the following actions:  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, and deploys the resulting assemblies.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.  

      You may receive the following or similar warnings during the setup process. You can safely ignore them.  

     ```  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\PartyResolution.sln" (Buildtarget) (1) ->  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5) ->  
     "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5:2) ->  
     (CompileODX target) ->  
       C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(831,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  
       C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(841,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  

     ```  

3. Start **Visual Studio Command Prompt**.  

4. Type the following commands to install the assemblies to the global assembly cache:  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Schemas\bin\Release\schemas.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Pipeline\projectschema\bin\Release\ProjectSchema.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Buyer\bin\Release\Buyer.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency1\bin\Release\ShipmentAgency1.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency2\bin\Release\ShipmentAgency2.dll  

   - gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Supplier\bin\Release\Supplier.dll  

5. Obtain a secured e-mail certificate from a certificate authority (CA). The CA could be a third-party authority or the authority within your organization. After you obtain the certificate, export the public key and private key.  

6. To import the private key to the Personal store of the Host instance logon account and the public key to the Local Computer Other People store, do the following:  

   1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand the BizTalk Group, and then expand **Platform Settings**.  

   2. Click on **Host Instances** and find the Logon account shown for the default In-Process host instance. In a default installation the default In-Process host should be named BizTalkServerApplication.  

   3. Click **Start**, and then click **Run**. In the **Run** box, type **mmc.exe**, and then click **OK**. Enter the correct password for the host instance logon account to open the Microsoft Management Console (MMC) under that account.  

   4. On the **File** menu, click **Add/Remove Snap-in**.  

   5. In the **Add or Remove Snap-ins** dialog box, select **Certificates**, and then click **Add**.  

   6. In the **Certificates snap-in** dialog box, select **My user account**, and then click **Finish**.  

   7. In the **Add or Remove Snap-ins** dialog box, select **Certificates**, and then click **Add**.  

   8. In the **Certificates snap-in** dialog box, select **Computer account**, and then click **Next**.  

   9. In the **Select Computer** dialog box, select **Local computer**, and then click **Finish**.  

   10. In the **Add or Remove Snap-ins** dialog box, click **OK**.  

   11. Expand the **Certificates - Current User** node and then expand **Personal**. Right-click **Certificates**, click **All Tasks**, and then click **Import**.  

   12. Import the private key and provide a password in the wizard.  

   13. Expand the **Certificates (Local Computer)** node and then expand **Other People**. Right-click **Certificates**, click **All Tasks**, and then click **Import**.  

   14. Import the public key.  

7. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **BizTalk Group** node and then click **Properties**. In the **BizTalk Group - Group Properties** dialog box, select **Certificate**.  

8. In the **Certificate** dialog box, click **Browse** and select the private key you just imported. The certificate specified here is used to sign the outbound message. Click **OK**.  

9. To update the BuyerAgency party in this sample do the following:  

   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, select **Parties**.  

   2. Right-click **BuyerAgency** and then click **Properties**. In the **BuyerAgency - Party Properties** dialog box, select **General**.  

   3. Under the **Aliases** section of the dialog, add a new alias with the name and qualifier set to **WindowsUser**. Set the Value to a user name in format of \<domain\user name> (e.g. SOMEDOMAIN\someuser).  

   4. Select **Certificate** and then click **Browse** and select the public key you just imported. The certificate specified here is used to validate the sender identity of the inbound message. Click **OK**.  

10. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, and then select **Hosts**.  

11. Right-click **BizTalkServerApplication** and then click **Properties**. In the **BizTalkServerApplication - Host Properties** dialog box, select **Certificates**.  

12. Click **Browse** and select the private key you just imported. The certificate specified here is used to decrypt the inbound messages. Click **OK**.  

13. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, and then select **Host Instances**.  

14. Right-click **BizTalkServerApplication** and then click **Restart**.  

## Running This Sample  

#### To run the PartyResolution sample  

1.  Run FilePolling.exe from the following folder:  

     *\<Samples Path>*\Orchestrations\PartyResolution\FilePolling\bin\Debug  

2.  Click **Start polling**.  

3.  Paste a copy of the provided PO instance file, PurchaseOrder.xml, in the following folder:  

     *\<Samples Path>*\Orchestrations\PartyResolution\FileDrop\PurchaseOrder  

4.  Observe the sequence of messages that are provided in the form of message boxes that keep you informed about the progress of the sample:  

    1.  When the supplier receives the PO from the buyer.  

    2.  When a shipment order request is received from shipment agency 1 or 2.  

    3.  When a shipment advice is received by shipment agency 1 or 2.  

    4.  When the supplier sends the PO delivery receipt to the buyer.  

5.  Click **Exit** to close the File Polling program.  

> [!NOTE]
>  You can edit the Country tag in PurchaseOrder.xml to "US" and then repeat step 2 and step 3. Observe that the shipment order is now sent to shipment agency 2.  

## Uninstalling This Sample  

#### To uninstall the PartyResolution sample  

1. At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*>\Orchestrations\ PartyResolution\\.  

2. Run Cleanup.bat.  

## See Also  
 [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md)   
 [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [Orchestrations (BizTalk Server Samples Folder)](../core/orchestrations-biztalk-server-samples-folder.md)