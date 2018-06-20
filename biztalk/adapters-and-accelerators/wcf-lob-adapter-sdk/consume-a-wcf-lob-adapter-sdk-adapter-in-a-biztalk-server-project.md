---
title: "Consume a WCF LOB Adapter SDK adapter in a BizTalk Server project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Consume a WCF LOB Adapter SDK adapter in a BizTalk Server project
This topic describes how to consume an adapter built using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  

> [!NOTE]
>  In order to use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you must install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tools on the same computer hosting [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  


## Use the Consume Adapter Service Add-in  


1. Open your .NET application in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  

2. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in the **Project** pane, right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project, and then choose **Add**&#124;**Add Generated Items** &#124; **Consume Adapter Service**.  

3. In the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] screen, select an adapter binding.  

4. Click **Configure** to configure the connection URI for the selected adapter binding and to provide any credentials, URI properties, and binding properties. Actual requirements will vary based on the selected adapter binding.  

5. Click **OK** when you have configured the URI.  

6. Click **Connect**. If the connection URI is valid and client credentials (if any) are accepted, the **Category** pane should be populated with the categories and operations provided by the adapter.  

7. If the adapter support search, the search field will be active. Otherwise, you can filter by contract type and explore types and operations by clicking nodes in the **Category** pane.  

8. Click **OK** to generate the proxy artifacts. The number of artifacts varies based on the contract type:  


   | Contract Type |  Artifact   |                         Description                         |                                                             |
   |---------------|-------------|-------------------------------------------------------------|-------------------------------------------------------------|
   |   Outbound    | XML Schemas | Contains the schemas for the selected types and operations. |                                                             |
   |   Outbound    |             |        WCF-Custom send port binding information XML         |  Contains configuration XML for the WCF-Custom send port.   |
   |    Inbound    | XML Schemas | Contains the schemas for the selected types and operations. |                                                             |
   |    Inbound    |             |       WCF-Custom receive port binding information XML       | Contains configuration XML for the WCF-Custom receive port. |


9. You can now use the XML Schema files in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.  

## Deploy the BizTalk Server project  

1. Open **BizTalk Server Administration**.  

2. Import the port binding XML file(s) to create the physical ports. Right-click your application under the **Applications** group, select **Import Bindings**, and then navigate to and select the appropriate port binding information XML file(s).  

3. Map the logical ports defined in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations to the newly created physical ports.  

4. Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Enlist**.  

5. Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Start**.  

6. Right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, and then click **Start**.  

## Generate Multiple Schemas  
 If you use the Consume Adapter Service Wizard to generate multiple schemas, one or more elements may be duplicated in the schemas resulting in compilation failure for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project. You can avoid this by selecting the **Generate Unique Schema Type** check box to ensure that schema types are generated with unique namespaces.  

## See Also  
 [Consume an adapter created using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)