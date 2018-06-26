---
title: "How to Configure Tracking for a Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, configuring"
  - "managing [schemas], configuring"
  - "configuring [HAT tracking], schemas"
  - "configuring, schemas"
  - "configuring, tracking"
  - "HAT, schemas"
  - "managing [schemas], tracking"
  - "schemas, tracking"
  - "tracking, configuring"
  - "tracking, schemas"
ms.assetid: b5f69c98-8824-43b1-8f21-d84b60ac5431
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Tracking for a Schema
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a schema. To configure tracking, you specify the properties of the messages that you want to view in the query views of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console Group Hub page.  
  
 For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md). For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. To you want to view tracking options only, you can be logged on as a member of the BizTalk Server Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for a schema  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to configure tracking, and then expand the application containing the schema.  
  
3. Click **Schemas**, right-click the schema, and then click **Properties**.  
  
4. In the left pane, click **Tracking**.  
  
5. Do one of the following to specify which properties to use for tracking messages, and then click **OK**:  
  
   -   Select the **Select all message properties** check box to use all the listed properties.  
  
       > [!NOTE]
       >  This check box is available only for schemas that contain promoted properties.  
  
   -   Select the check box of each property that you want to use.  
  
       > [!NOTE]
       >  This is available only for schemas that contain promoted properties.  
  
> [!NOTE]
>  You should select only the options you need, as tracking messages creates performance and storage overhead for your system.  
  
## See Also  
 [Managing Schemas](../core/managing-schemas.md)