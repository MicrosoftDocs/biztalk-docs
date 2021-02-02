---
description: "Learn more about: Step 1: Configure a FILE Receive Location"
title: "Step 1: Configure a FILE Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df591263-964a-4ad8-bc3a-a553de8dae4f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure a FILE Receive Location
In this topic, you configure a FILE receive location that consumes the dummy request message that you drop to a file folder to invoke the send port.  
  
> [!NOTE]
>  The steps in this tutorial assume that you use the default application (**BizTalk Application 1**) to create the solution. You can also create another application and perform the same steps in any that application.  
  
### To configure a FILE receive location  
  
1.  From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  
  
2.  On the General tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **ReceivePortRestAzureMarketPlace**.|  
    |**Enable routing for failed messages**|(clear)|  
  
3.  Click **Receive Locations**, and then click **New**.  
  
4.  From Receive Location1 – Receive Location Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Name**|Type **ReceiveLocationAzureMarketPlace**.|  
    |**Type**|Select **FILE**.|  
    |**Receive handler**|Select **BizTalkServerApplication**.|  
    |**Receive pipeline**|Select **PassThruReceive**.|  
  
5.  Click **Configure**.  
  
6.  From File Transport Properties, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Receive folder**|Type a location where you will drop the dummy request message.|  
    |**File name**|Retain `*.xml`|  
  
7.  Click **OK** until you exit all the dialog boxes.  
  
## See Also  
 [Tutorial 5: Invoking a REST Interface Using BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)
