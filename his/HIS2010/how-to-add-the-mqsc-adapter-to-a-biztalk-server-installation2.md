---
title: "How to Add the MQSC Adapter to a BizTalk Server Installation2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a306551-4731-4d87-a5e9-3061ef11db84
caps.latest.revision: 3
---
# How to Add the MQSC Adapter to a BizTalk Server Installation
When you install the BizTalk Adapter for WebSphere MQ (MQSC Adapter), the BizTalk Adapters for Host Systems installation process adds the adapter to your BizTalk Server installation by default. Following installation, if for any reason the adapter is missing from the BizTalk Server 2006 Administration Console (for example, if it was deleted during testing), you can add it manually by using the following procedure.  
  
### To add the MQSC adapter  
  
1.  In the Console Root of the BizTalk Server 2006 Administration Console, expand the **BizTalk Server 2006 Administration** node.  
  
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
 [BizTalk Adapter for WebSphere MQ](../HIS2010/biztalk-adapter-for-websphere-mq1.md)   
 [How to Install the MQSC Adapter &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/a148aefc-1224-401e-9f68-0606b32b7877)