---
description: "Learn more about: Develop BizTalk applications using the Siebel adapter"
title: "Develop BizTalk applications using the Siebel adapter"
ms.custom: ""
ms.date: "08/02/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Develop BizTalk applications using the Siebel adapter

## Overview
Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate XML schema. Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.  
  
 CBR can be used in scenarios where the messages being sent to a Siebel system do not require any intensive processing. For example, if you know that the receive port will be receiving messages only of a certain type, you can add a filter to the send port to route the messages matching the filter expression to the send port.  
  
 In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. This section provides information about using BizTalk orchestrations to perform operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] that can interact with a WCF binding.  

## Before you begin  

* To use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], always set the **EnableBizTalkCompatibilityMode** binding property to **True**. For the steps, see [Configure the binding properties for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).
  
* The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not automatically listed in the BizTalk Server Administration console. This is because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] is a WCF custom binding. 

* To generate metadata, use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. Do not use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. For instructions on using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).   

  
## See Also  
[Develop your Siebel applications](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)
