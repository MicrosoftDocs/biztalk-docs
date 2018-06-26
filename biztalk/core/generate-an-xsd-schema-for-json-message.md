---
title: "Generate an XSD schema for JSON message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5453b76c-b282-442f-9eb1-6c2628b38ad5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate an XSD schema for JSON message
> [!NOTE]
>  This tutorial applies to BizTalk Server only.  
  
 In this solution, a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application receives a JSON message. Before the application can process the message, it must be converted to an XSD schema. To do so, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a JSON Schema Wizard that creates an XSD schema from a JSON message.  
  
1. In Visual Studio, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.  
  
2. In the Solution Explorer, right-click the project name > **Add** > **New Item** > **JSON Schema Wizard**. Provide a name for the schema (`PO.xsd`), and then click **Add**.  
  
3. In the JSON Schema Wizard, on the welcome page, click **Next**.  
  
4. In the JSON Schema Information page, provide the location of the JSON purchase order file that is sent to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application. Provide a root node name, a target namespace, and then click **Finish**.  
  
    ![Generated XSD schema for JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")  
  
5. A schema with the specified name is added to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project. The generated schema file (**PO.xsd**) is also provided with the sample.  
  
## See Also  
 [Processing JSON messages using BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)