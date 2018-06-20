---
title: "Step 6: Configuring Orchestration Shapes (Contoso) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, configuring shapes"
  - "private process tutorial, configuring orchestration shapes"
ms.assetid: ce680693-cf72-4ca6-a062-019de5a9257b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Configuring Orchestration Shapes (Contoso)
In this step, you configure the orchestration shapes you added to the PrivateResponder orchestration that you created in [Step 5: Modifying the Contoso Private Process Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md). This includes setting up the communication between [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server and the Enterprise Resource Planning (ERP) system for Contoso.  
  
### To configure the ConstructMessagePIP3A2RequestMessage shape  
  
1.  With PrivateResponder.odx selected in Solution Explorer, on the orchestration design surface, select the **ConstructPIP3A2RequestMessage** shape.  
  
2.  In the Properties window, select the **Messages Constructed** property, select **PIP3A2RequestMessage** from the drop-down list, and then press **Enter**.  
  
3.  Double-click the **Message Assignment** shape in the **ConstructPIP3A2RequestMessage** shape to open BizTalk Expression Editor.  
  
4.  In BizTalk Expression Editor, type the following:  
  
    ```  
    PIP3A2RequestMessage = Helper.NormalizeHeader(Microsoft.Solutions.BTARN.Shared.SCContainer.ConvertFromContainer(ActionMessage));  
    ```  
  
5.  Click **OK**.  
  
### To configure the ConstructContoso3A2RequestMessage Transform shape  
  
1.  On the orchestration design surface, click the **ConstructContoso3A2RequestMessage** shape.  
  
2.  In the Properties window, select the **Message Constructed** property, and then select **Contoso3A2RequestMessage** from the drop-down list.  
  
3.  Select the **Transform_1** shape within the **ConstructContoso3A2RequestMessage** shape.  
  
4.  In the Properties window, select the **Map Name** property, and then click the ellipsis button (**…**) to open the Transform Configuration dialog box.  
  
5.  In the Transform Configuration dialog box, click **Existing Map**, and then in the **Fully Qualified Map Name box**, select **\<Select from Referenced Assembly\>** from the drop-down list to open the Select Artifact Type dialog box.  
  
6.  In the Select Artifact Type dialog box, select the **ContosoPriceAndAvailability** assembly in the left pane, select **PIP3A2RequestToContosoPriceRequest** map in the right pane, and then click **OK**.  
  
7.  In the Transform Configuration dialog box, select **Source** in the left pane.  
  
8.  Click the empty box under **Variable Name**, and then select **PIP3A2RequestMessage** from the drop-down list.  
  
9. Select **Destination** in the left pane, click **Contoso3A2RequestMessage** from the **VariableName** drop-down list, and then click **OK**.  
  
### To configure the Execute3A2Vocabulary Call Rules shape  
  
1.  On the orchestration design surface, double-click the **Execute3A2Vocabulary** shape within the **Scope_1** shape.  
  
2.  In the CallRules policy configuration dialog box, select **3A2PriceAvailabilityPolicy** from the **Select the business policy that you wish to call** drop-down list.  
  
3.  In the **Specify policy parameters** list, click **Click here to add a new row**, and then select **Contoso3A2ResponseMessage** from the drop-down list.  
  
4.  Click **OK**.  
  
### To configure the Construct3A2ResponseMessage Transform shape  
  
1. On the orchestration design surface, click the **Construct3A2ResponseMessage** shape.  
  
2. In the Properties window, select the **Messages Constructed** property, and then select **PIP3A2ResponseMessage** from the drop-down list, and then press **Enter**.  
  
3. Select the **Transform_2** shape within the **Construct3A2ResponseMessage** shape.  
  
4. In the Properties window, click **Map Name**, and then click the ellipsis button (**…**).  
  
5. In the Transform Configuration dialog box, click **New Map.**  
  
6. In the **Fully Qualified Map Name** box, type **ContosoPriceAndAvailability.ContosoResponse3A2RequestMerge**.  
  
7. In the Transform Configuration dialog box, select **Source** in the left pane.  
  
8. Click the **Click here to add a new row** label under **Variable Name**, and then select **PIP3A2RequestMessage** from the drop-down list.  
  
9. Click the **Click here to add a new row** label under **Variable Name** on the next line, and then select **Contoso3A2ResponseMessage** from the drop-down list.  
  
10. Select **Destination** in the left pane, select **PIP3A2ResponseMessage** from the **Variable Name** drop-down list, and then click **OK**.  
  
11. In Solution Explorer, right-click the **ContosoResponse3A2RequestMerge.btm** file, and then click **Open With**.  
  
12. In the **Open With - ContosoResponse3A2RequestMerge.btm** dialog box, select **XML Editor** from the list of programs, and then click **OK**. Click **Yes**.  
  
    > [!NOTE]
    >  Due to the large number of links required for this map, this tutorial uses [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 2008 HTML/XML Editor to construct the map by copying the map information manually.  
  
13. On the **Edit** menu, click **Select All**.  
  
14. Copy the following XML to the clipboard. On the **Edit** menu, click **Paste** to overwrite the current map:  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <!-- Generated using BizTalk Mapper on Mon, Nov 08 2004 06:20:59 PM -->  
    <!-- Copyright (c) Microsoft Corporation.  All rights reserved. -->  
    <mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes"><SrcTree><xs:schema xmlns:tns="http://schemas.microsoft.com/BizTalk/2003/aggschema" xmlns:ns2="http://Contoso.com/Price" xmlns:ns1="http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/2003/aggschema" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:import schemaLocation="Microsoft.Solutions.BTARN.Schemas.RNPIPs._3A2PriceAndAvailabilityQueryMessageGuideline_v1_3" namespace="http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd"/>  
    <xs:import schemaLocation="ContosoPriceAndAvailability.ContosoPriceSchema" namespace="http://Contoso.com/Price"/>  
    <xs:element name="Root">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element name="InputMessagePart_0">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element ref="ns1:Pip3A2PriceAndAvailabilityQuery"/>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    <xs:element name="InputMessagePart_1">  
    <xs:complexType>  
    <xs:sequence>  
    <xs:element ref="ns2:rootPriceResponse"/>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    </xs:sequence>  
    </xs:complexType>  
    </xs:element>  
    </xs:schema></SrcTree><TrgTree RootNode_Name="Pip3A2PriceAndAvailabilityResponse"><Reference Location="Microsoft.Solutions.BTARN.Schemas.RNPIPs._3A2PriceAndAvailabilityResponseMessageGuideline_v1_3"/></TrgTree><ScriptTypePrecedence><CSharp Enabled="Yes"/><ExternalAssembly Enabled="Yes"/><VbNet Enabled="Yes"/><JScript Enabled="Yes"/><XsltCallTemplate Enabled="Yes"/><Xslt Enabled="Yes"/></ScriptTypePrecedence><TreeValues><TestValues/><ConstantValues/></TreeValues><Pages><Page Name="Page 1"><Links><Link LinkID="1" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='GlobalProductStatusCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='GlobalProductStatusCode']" Label=""/><Link LinkID="2" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='GlobalCurrencyCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='GlobalCurrencyCode']" Label=""/><Link LinkID="3" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='GlobalProductIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='GlobalProductIdentifier']" Label=""/><Link LinkID="4" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="5" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='ProprietaryProductIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='ProductIdentification']/*[local-name()='PartnerProductIdentification']/*[local-name()='ProprietaryProductIdentifier']" Label=""/><Link LinkID="6" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='LineNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='LineNumber']" Label=""/><Link LinkID="7" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='GlobalPricingTypeCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='GlobalPricingTypeCode']" Label=""/><Link LinkID="8" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='thisDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='requestingDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" Label=""/><Link LinkID="9" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='thisDocumentGenerationDateTime']/*[local-name()='DateTimeStamp']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='requestingDocumentDateTime']/*[local-name()='DateTimeStamp']" Label=""/><Link LinkID="10" LinkFrom="1" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='thisDocumentIdentifier']/*[local-name()='ProprietaryDocumentIdentifier']" Label=""/><Link LinkID="11" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalLocationIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalLocationIdentifier']" Label=""/><Link LinkID="12" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='cityName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='cityName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="13" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine1']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine1']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="14" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine2']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine2']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="15" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine3']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='addressLine3']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="16" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalCountryCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='GlobalCountryCode']" Label=""/><Link LinkID="17" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='NationalPostalCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='NationalPostalCode']" Label=""/><Link LinkID="18" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailabilityQuery']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='regionName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseAddress']/*[local-name()='PhysicalAddress']/*[local-name()='regionName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="19" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" Label=""/><Link LinkID="20" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="21" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" Label=""/><Link LinkID="22" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" Label=""/><Link LinkID="23" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="24" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" Label=""/><Link LinkID="25" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" Label=""/><Link LinkID="26" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='GlobalPartnerRoleClassificationCode']" Label=""/><Link LinkID="27" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='GlobalPartnerClassificationCode']" Label=""/><Link LinkID="28" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalBusinessIdentifier']" Label=""/><Link LinkID="29" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='PartnerDescription']/*[local-name()='BusinessDescription']/*[local-name()='GlobalSupplyChainCode']" Label=""/><Link LinkID="30" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='contactName']/*[local-name()='FreeFormText']" Label=""/><Link LinkID="31" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='telephoneNumber']/*[local-name()='CommunicationsNumber']" Label=""/><Link LinkID="32" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_0']/*[local-name()='Pip3A2PriceAndAvailabilityQuery']/*[local-name()='toRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='fromRole']/*[local-name()='PartnerRoleDescription']/*[local-name()='ContactInformation']/*[local-name()='EmailAddress']" Label=""/><Link LinkID="33" LinkFrom="2" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='thisDocumentGenerationDateTime']/*[local-name()='DateTimeStamp']" Label=""/><Link LinkID="34" LinkFrom="3" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='GlobalDocumentFunctionCode']" Label=""/><Link LinkID="35" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='Price']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='productUnit']/*[local-name()='ProductPackageDescription']/*[local-name()='unitPrice']/*[local-name()='FinancialAmount']/*[local-name()='MonetaryAmount']" Label=""/><Link LinkID="36" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='NumberAvailable']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='ProductLineItem']/*[local-name()='ProductQuantity']" Label=""/><Link LinkID="37" LinkFrom="/*[local-name()='<Schema>']/*[local-name()='Root']/*[local-name()='InputMessagePart_1']/*[local-name()='rootPriceResponse']/*[local-name()='Products']/@*[local-name()='NumberAvailable']" LinkTo="/*[local-name()='<Schema>']/*[local-name()='Pip3A2PriceAndAvailabilityResponse']/*[local-name()='ProductPriceAndAvailability']/*[local-name()='WarehouseInformationResource']/*[local-name()='warehouseQuantity']/*[local-name()='ProductQuantity']" Label=""/></Links><Functoids><Functoid FunctoidID="1" X-Cell="52" Y-Cell="231" Functoid-FID="260" Functoid-Name="Scripting" Label=""><Input-Parameters/><ScripterCode><Script Language="CSharp"><![CDATA[///*Uncomment the following code for a sample Inline C# function  
    //that concatenates two inputs. Change the number of parameters of  
    //this function to be equal to the number of inputs connected to this functoid.*/  
  
    public string returnGUID()  
    {  
    return System.Guid.NewGuid().ToString();  
    }]]></Script></ScripterCode></Functoid><Functoid FunctoidID="2" X-Cell="55" Y-Cell="236" Functoid-FID="260" Functoid-Name="Scripting" Label=""><Input-Parameters/><ScripterCode><Script Language="CSharp"><![CDATA[public string GetRNDateTime()  
    {  
    DateTime dt;  
    dt=DateTime.UtcNow;  
    string dateVal = dt.ToString("u");  
    dateVal = dateVal.Replace("-","");  
    dateVal = dateVal.Replace(":","");  
    dateVal  =dateVal.Replace(" ","T");  
    string sec = "."+ DateTime.UtcNow.Millisecond.ToString()+"Z";  
    dateVal  =dateVal.Replace("Z",sec);  
    return  dateVal;  
    }]]></Script></ScripterCode></Functoid><Functoid FunctoidID="3" X-Cell="54" Y-Cell="239" Functoid-FID="107" Functoid-Name="String Concatenate" Label=""><Input-Parameters><Parameter Type="Constant" Value="Response" Guid="{FA85B113-6FB4-4932-A125-5CF751A536B5}"/></Input-Parameters></Functoid></Functoids></Page></Pages></mapsource>  
    ```  
  
15. On the **File** menu, click **Save All**.  
  
### To configure the Expression_1 shape  
  
1.  In Solution Explorer, double-click **PrivateResponder.odx**.  
  
2.  On the orchestration design surface, double-click the **Expression_1** shape to open BizTalk Expression Editor.  
  
3.  In BizTalk Expression Editor, type the following code:  
  
    ```  
    contosoResponseXML = PIP3A2ResponseMessage;  
  
    submitMessage.SubmitMessage(  
      Microsoft.Solutions.BTARN.Shared.MessageCategory.AsyncResponse,  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCDestinationPartnerID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCSourcePartnerID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCInstanceID),  
    ActionMessage(Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPVersion),   
    Helper.ReturnSCWithDocType(contosoResponseXML) );  
    ```  
  
4.  Click **OK**.  
  
## See Also  
 [Step 7: Creating and Configuring Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)