---
title: "Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration, SAP Receive IDOC BizTalk project"
  - "migrating, SAP Receive IDOC BizTalk project"
  - "migration"
ms.assetid: 74b667d8-2d8c-4c15-9dd2-f13521404b85
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project
The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:  
  
- The design-time experience of creating a BizTalk project.  
  
- The metadata retrieval experience.  
  
- Schema file name and namespace.  
  
- Data type mappings.  
  
- The operations that can be performed using the adapter.  
  
- Physical port configuration in the BizTalk Server Administration console.  
  
  These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).  
  
  However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
  This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.  
  
> [!NOTE]
>  In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter. Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.  
  
## Sample Used for the Tutorial  
 This tutorial is based upon a sample (ReceiveIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that receives a flat-file IDOC from an SAP system. The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## Prerequisites  
  
-   You must have a vPrev BizTalk project. This tutorial involves a BizTalk project that receives an ORDERS03 IDOC from an SAP system.  
  
-   [Create strong-name key file, and learn the tools](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## Understanding a BizTalk Project Created Using the Previous Version of the Adapter  
 The key constituents of a vPrev BizTalk project to receive an IDOC are:  
  
-   **BizTalk orchestration**. This is a simple orchestration that consists of an SAP receive port that receives a flat-file IDOC from an SAP system. The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration. Before the XML IDOC is copied to a file location through a file port, it is converted back into a flat-file IDOC using a flat-file assembler.  
  
-   **Schema for the IDOC you want to send to the SAP system**. This tutorial involves a BizTalk project that receives ORDERS03 IDOC from the SAP system. The schema generated for the IDOC is ORDERS03.xsd. This schema is generated using the vPrev SAP adapter.  
  
## How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter  
 The goal of this migration tutorial is to enable you to receive a flat-file IDOC from an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter. Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration.  
  
- A vPrev SAP receive port that receives a flat-file IDOC from an SAP system. The port also converts this to an XML IDOC using a flat-file disassembler, which is available as part of the vPrev BizTalk application. The XML IDOC conforms to the schema (ORDERS03.xsd) that you generated using the vPrev SAP adapter.  
  
- A file send port which copies the IDOC to folder. This port also uses the flat-file assembler pipeline, available in the BizTalk application, to convert the XML IDOC to a flat-file IDOC.  
  
  To migrate your existing vPrev BizTalk project, you do not need to change the file send port that copies the flat-file IDOC to a folder. You only need to configure a new WCF-Custom receive port with the right configuration settings. This tutorial demonstrates how to configure the WCF-Custom receive port to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## In This Section  
  
-   [Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [Step 2: Configure a WCF-Custom One-way Receive Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## See Also  
 [SAP Adapter Tutorials](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)