---
title: "Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, creating LOB maps"
ms.assetid: a947e0ac-f0cb-4be9-85a8-09daf3675b1a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper
In this step, you create two maps that define the transformation required to successfully exchange messages between the two trading partners. For this scenario, the Contoso ERP system has already standardized on a message format for a Price and Availability request. The two maps will map the request and response messages from the trading partner, Fabrikam, to and from those internally defined Contoso messages, respectively.  
  
### To add a reference for the 3A2 PriceAndAvailability Request schema  
  
1.  In Solution Explorer, right-click the ContosoPriceAndAvailability project, and then click **Add Reference**.  
  
2.  In the Add Reference dialog box, click **Browse**.  
  
3.  Move to the folder *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin, and then select the **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll** assembly.  
  
4.  Click **Add**, and then click **OK**.  
  
### To create the 3A2 PriceAndAvailability request to Contoso PriceAndAvailability request map  
  
1.  In Solution Explorer, right-click the ContosoPriceAndAvailability project, point to **Add**, and then click **New Item**.  
  
2.  In the Add New Item - ContosoPriceAndAvailability dialog box, select **Map Files** in the Categories pane, and then select **Map** in the **Templates** pane. In the **Name** box, type **PIP3A2RequestToContosoPriceRequest**, and then click **Add**.  
  
### To associate the schemas for the PIP3A2RequestToContosoPriceRequest map  
  
1.  In BizTalk Mapper (with PIP3A2RequestToContosoPriceRequest.btm displayed), in the Source Schema pane, click **Open Source Schema**.  
  
2.  In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, and then expand **Schemas.**  
  
3.  Select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.**  
  
     **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3**, and then click **OK**.  
  
4.  In the Destination Schema pane, click **Open Destination Schema**.  
  
5.  In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, and then expand **Schemas**.  
  
6.  Select the **ContosoPriceAndAvailability.ContosoPriceSchema** schema, and then click **OK**.  
  
7.  In the Root Node for Target Schema dialog box, select the **rootPriceRequest** schema, and then click **OK**.  
  
### To link schema fields in the PIP3A2RequestToContosoPriceRequest map  
  
1.  In the Destination Schema pane, right-click the **\<Schema\>** node, and then click **Expand Tree Node**.  
  
2.  In the Source Schema pane, right-click the **\<Schema\>** node, and then click **Expand Tree Node**.  
  
3.  Drag the **GlobalProductIdentifier** field to the **ProductID** field in the Destination Schema pane.  
  
    > [!NOTE]
    >  You can find the **GlobalProductIdentifier** field in the node Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery/  
    >   
    >  ProductPriceAndAvailability/ProductLineItem/productUnit/  
    >   
    >  ProductPackageDescription/ProductIdentification.  
  
4.  On the **File** menu, click **Save All** to save your changes.  
  
## See Also  
 [Creating and Configuring BizTalk Ports for Contoso](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)