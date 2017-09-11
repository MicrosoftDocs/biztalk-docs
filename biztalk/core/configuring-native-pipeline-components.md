---
title: "Configuring Native Pipeline Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pipeline Designer, pipeline components"
  - "pipeline components, configuring"
  - "Pipeline Designer, code sample"
  - "IPersistPropertyBag interface"
ms.assetid: a3332a60-8cd6-43fa-9ecf-e1e54e71fef7
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Native Pipeline Components
Pipeline components can expose their own custom properties at design time. Any public property defined in the component will be rendered in Pipeline Designer providing that read and write accessors for that property are implemented. Pipeline Designer will display the component properties in accordance with their declaration; for example, if the property is declared as read-only, it will be displayed as such in Pipeline Designer.  
  
 Custom pipeline components must implement the **IPersistPropertyBag** interface to enable the creation of these custom properties. Properties created with the **IPersistPropertyBag** interface can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], just like all the properties of the native pipeline components. This section contains procedures for configuring each of the included pipeline components.  
  
## In This Section  
  
-   [How to Configure Native Pipeline Components](../core/how-to-configure-native-pipeline-components.md)  
  
-   [How to Configure the BizTalk Framework Assembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)  
  
-   [How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)  
  
-   [BizTalk Framework Schema and Properties](../core/biztalk-framework-schema-and-properties.md)  
  
-   [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)  
  
-   [How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)  
  
-   [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)  
  
-   [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)  
  
-   [MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)  
  
-   [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
  
-   [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md)  
  
-   [How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)  
  
-   [XML and Flat File Property Schema and Properties](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
-   [How to Configure the XML Validator Pipeline Component](../core/how-to-configure-the-xml-validator-pipeline-component.md)