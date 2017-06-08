---
title: "How to Create an Adapter Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, handlers [adapters]"
  - "handlers [adapters], creating"
  - "adapters, handlers"
ms.assetid: 09569417-dce6-473d-891f-6fd12347bcf0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create an Adapter Handler
You can create a send or receive adapter handler by using the BizTalk Server Administration Console.  
  
> [!NOTE]
>  You must be a member of the Single Sign-On Administrators group to create an adapter handler.  
  
### To create an adapter handler  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2.  In the expanded adapter list, right-click the adapter for which you would like to add a send or receive handler, point to **New**, and then click **Send Handler** to create a send handler or click **Receive Handler** to create a receive handler.  
  
3.  In the **\<host name> Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the adapter handler will be associated.  
  
4.  If you are creating an adapter send handler, select the option to **Make this the default handler** if you would like for this to be the default send handler for this adapter.  
  
5.  Click **OK**.  
  
## See Also  
 [Creating and Deleting Adapter Handlers](../core/creating-and-deleting-adapter-handlers.md)