---
title: "Static Design-Time Adapter Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332723a4-e39d-43f5-af4d-bf9f56496535
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Static Design-Time Adapter Configuration
The design-time part of the adapter is responsible for defining all the available properties and for validating user input. In a static design-time configuration the adapter uses the default user interface (UI) for displaying and editing its properties.  
  
 This section explains how to implement static design-time configuration capability for your custom adapter. The changes you decide to make will be based on the needs of the applications with which the adapter communicates and the logic that the adapter needs to implement. Links to sections of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help that describe these steps in more detail or provide additional background are provided when available. Additionally it calls out the places in the sample file adapter documentation that provide relevant examples.  
  
## Guidelines for the Static Development Process  
 The following list provides recommendations for building static design-time functionality into your adapter. During development you may not need to do all of these steps, nor execute them in a rigid sequence.  
  
1. Create a list of adapter configuration requirements and configuration parameters that you need to set. If the parameters are globally used for all receive locations and send ports, specify them in the handler schema configuration file. If they are port or location specific, configure them in the send port and receive location configuration files.  
  
2. Modify the adapter property pages to account for any new configuration parameters. For information about this step, see [Adapter Configuration Schemas](../core/adapter-configuration-schemas.md).  
  
3. Modify the tree view of the schema categories by using the Add Adapter Metadata Wizard. For more information about this step, see [Schema Categories in the Add Adapter Metadata Wizard](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)  
  
4. Modify the sample code to return schemas as Web Services Description Language (WSDL) files. For more information about this step, see [Static Adapter IStaticAdapterConfig Interface](../core/static-adapter-istaticadapterconfig-interface.md).  
  
5. Modify the existing WSDL files or create new WSDL files. For more information about this step, see [Adapter WSDL Files](../core/adapter-wsdl-files.md).  
  
6. Modify the sample code to return additional XSD files needed by the adapter that are not included in the WSDL files. For more information about this step, see [Adapter GetSchema Method](../core/adapter-getschema-method.md).  
  
7. Modify the adapter registry keys and run the adapter registry file. For more information about this step, see [Adapter Registration File](../core/adapter-registration-file.md).  
  
8. Install the static adapter into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information about this step, see [Install the Adapter into BizTalk Server](../core/install-the-adapter-into-biztalk-server.md).  
  
9. Test the changes made to the adapter property pages. Rebuild the adapter to test the UI that appears in the Add Adapter Metadata Wizard. For more information about this step, see [Build and Test the Adapter Project](../core/build-and-test-the-adapter-project.md)  
  
## In This Section  
  
-   [Static Adapter IStaticAdapterConfig Interface](../core/static-adapter-istaticadapterconfig-interface.md)  
  
-   [Schema Categories in the Add Adapter Metadata Wizard](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)