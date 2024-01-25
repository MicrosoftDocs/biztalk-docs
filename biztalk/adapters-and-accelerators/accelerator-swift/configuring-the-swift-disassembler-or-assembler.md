---
description: "Learn more about: Configuring the SWIFT Disassembler or Assembler"
title: "Configuring the SWIFT Disassembler or Assembler"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring the SWIFT Disassembler or Assembler
After you add the SWIFT disassembler or SWIFT assembler to a custom pipeline, you must configure it to provide the functionality you want for the particular scenario (such as enabling/disabling dynamic message type discovery, inbound debatching, XML validation, Business Rule Engine (BRE) validation, and so on). You must configure the SWIFT disassembler and assembler during development time before you compile and deploy the custom pipelines that invoke them. To configure the SWIFT disassembler/assembler, select the component in Pipeline Designer and edit the configuration properties in the Properties window.  
  
 Refer to [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md) for complete details and descriptions for each configuration property, as well as other usage and configuration information.  
  
 Refer to [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md) for complete details and descriptions for the Encoding Charset configuration property, as well as other usage and configuration information.  
  
> [!NOTE]
>  After you configure, compile, and deploy the custom pipelines, changes in configuration will require re-compiling and re-deployment of the custom pipelines.  
  
 After you configure, compile, and deploy your custom pipelines for processing SWIFT messages, you can set up receive locations that use your custom SWIFT receive pipeline, and send ports that use your custom SWIFT send pipeline. For more information about deploying pipelines and configuring receive ports, receive locations, and send ports, see [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md), [Module 5: Creating Flat File Receive and XML Send Ports](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md), and BizTalk Server Help.  
  
 This section contains:  
  
-   [Configuring the SWIFT Disassembler](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)  
  
-   [Configuring the SWIFT Assembler](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)  
  
## See Also  
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)
