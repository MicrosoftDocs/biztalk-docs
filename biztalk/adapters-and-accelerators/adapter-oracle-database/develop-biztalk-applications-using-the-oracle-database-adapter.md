---
title: "Develop BizTalk applications using the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Content-Based Routing (CBR)"
  - "BizTalk orchestrations, using orchestrations to perform operations"
ms.assetid: 65689c83-4a57-4aad-b0e9-f1bad901a7b9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop BizTalk applications using the Oracle Database adapter
Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate XML schema. Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.  
  
 CBR can be used in scenarios where the messages being sent to the Oracle database do not require any intensive processing. For example, if you know that the receive port will be receiving messages only of a certain type, you can add a filter to the send port to route the messages matching the filter expression to the send port.  
  
 In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. This section provides information about using BizTalk orchestrations to perform operations on the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which can interact with a WCF binding.  
  
> [!IMPORTANT]
>  To use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**. For instructions about how to set the binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
> 
> [!IMPORTANT]
>  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] included with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] is not listed in the BizTalk Server Administration console. The adapters in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] are WCF-based, and use a WCF custom binding. The BizTalk Server Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]. It does not automatically display the WCF custom bindings and therefore does not display the WCF based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
> 
> Also, to generate metadata, use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. Do not use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. For instructions on using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md). 
> 
> For other differences between the adapter versions, see [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
  
  
## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)