---
title: "Features for Siebel adapter clients | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapter features"
  - "features, of the adapter"
ms.assetid: 11792629-a692-4378-b522-d33484ee8acb
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Features for Siebel adapter clients
In addition to the features discussed throughout the topics of [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md), the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides the following features that are useful for adapter clients:  
  
- **Support for configuring adapters using binding properties**. Adapter clients can configure the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] by specifying certain binding properties while generating the metadata. For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
- **Support for null values for operation parameters**. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to provide null values for business object operation parameters using the XSD "nillable" attribute. The adapter does not pass fields with null values to the Siebel system.  
  
- **Support for XML data streaming**. Adapter clients can stream data from or to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] by using the **XMLReader** or **XMLWriter** interfaces.  
  
- **Support for dynamic ports in BizTalk Server**. Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties. For more information, see [Configuring dynamic ports with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/configure-dynamic-ports-with-the-siebel-adapter.md).  
  
- **Support for message versioning**. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports message versioning. This enables support for different message schemas in future releases of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information, see [Message Versioning Support](../../adapters-and-accelerators/adapter-siebel/message-versioning-support2.md).  
  
- **Support for performance counters**. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports WCF-based performance counters that adapter clients can use. For more information about performance counters, see [Use Performance Counters with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-performance-counters-with-the-siebel-adapter.md).  
  
  > [!NOTE]
  >  This feature does not provide backward compatibility with the earlier versions of the adapter.  
  
- **Support for encoding XML element names**. The[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] presents entities from enterprise applications as element names in XML. Underscores are the only special characters that can be included in the element names. Therefore, underscores are used to encode element names with special characters. For example, `emp$name` is encoded to `emp_x0024_name`.  
  
## See Also  
 [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)