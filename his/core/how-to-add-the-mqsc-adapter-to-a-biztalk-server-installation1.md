---
title: "How to Add the MQSC Adapter to a BizTalk Server Installation | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6220e81-5176-4588-92e9-67bf73d46067
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Add the MQSC Adapter to a BizTalk Server Installation
When you install the BizTalk Adapter for WebSphere MQ (MQSC Adapter), the BizTalk Adapters for Host Systems installation process adds the adapter to your BizTalk Server installation by default. Following installation, if for any reason the adapter is missing from the BizTalk Server Administration Console (for example, if it was deleted during testing), you can add it manually by using the following procedure.  
  
## Add the MQSC adapter  
  
1.  Open the **BizTalk Server Administration** console.  
  
2.  Expand the **BizTalk Group** node.  
  
3.  Expand the **Platform Settings** node.  
  
4.  Right-click **Adapters**.  
  
5.  Click **New**.  
  
     The Adapter Properties window is displayed.  
  
6.  In the **Name** field, type a name for the adapter.  
  
7.  In the **Adapter** field, select **MQSC** in the list.  
  
8.  In the **Description** box, type any text that is useful to you. (This is an optional step.)  
  
9. Click **OK**.  
  
    > [!NOTE]
    >  Adding the adapter requires that you restart the host instance.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)   