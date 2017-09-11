---
title: "Configure the Siebel Adapter to Integrate the Siebel System with the Business Data Catalog and SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49b575e8-5f33-4e6e-a914-95d357671ab5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the Siebel Adapter to Integrate the Siebel System with the Business Data Catalog and SharePoint
The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] includes the [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)], which generates a WCF service for specific LOB artifacts. This WCF service is hosted in a hosting environment such as Microsoft Internet Information Services (IIS). The Business Data Catalog Definition Editor uses the URL where the WCF service is hosted to get the Web Services Description Language (WSDL) for the WCF service. Using the WSDL, the Business Data Catalog Definition Editor extracts the methods available to the WCF service. These methods can be used to establish entities and the association between the entities.  
  
 The Business Data Catalog Definition Editor helps you create an application definition file (an XML file) that Microsoft Office SharePoint Server can consume. Once the application definition file is imported to Microsoft Office SharePoint Server, you can create Web Parts to present the information from enterprise applications. For more information, see “Creating Web Parts” in [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
## Tutorial  
 To demonstrate how to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server, the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] includes a tutorial that provides step-by-step instructions to present data from a Siebel system on a SharePoint site. See [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
## See Also  
 [Use the Siebel Adapter with SharePoint](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)