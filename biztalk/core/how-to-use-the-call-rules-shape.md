---
title: "How to Use the Call Rules Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Call Rules shape [Orchestration Designer], how to"
  - "Call Rules shape [Orchestration Designer], configuring"
  - "Call Rules shape [Orchestration Designer], policies"
  - "policies, Call Rules shape [Orchestration Designer]"
ms.assetid: e4bc8a2c-de7e-4e3a-81b8-12bcebb17d27
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the Call Rules Shape
In Orchestration Designer, you can use the **Call Rules** shape to call a business policy.  
  
### To configure the Call Rules shape  
  
1. From the Toolbox, in the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line on the Orchestration Design Surface.  
  
    —Or—  
  
    Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape** on the context menu, and then click **Call Rules**.  
  
   > [!NOTE]
   >  In BizTalk Server, you do not need to have an atomic scope to insert a **Call Rules** shape. You can drag a **Call Rules** shape into the Orchestration Design Surface from the Toolbox. However, in BizTalk Server, the **Call Rules** menu item is disabled in the context menu if you try to insert a **Call Rules** shape inside an orchestration that does not have an atomic scope. This is a limitation with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product.  
  
2. In Orchestration Designer, select the **Call Rules** shape.  
  
3. Double-click the shape to display the **CallRules policy configuration** dialog box.  
  
4. In the **Select the business policy you wish to call** drop-down list, select the policy you need.  
  
   > [!NOTE]
   >  Call Rules configuration will look at the latest saved version of a policy when determining the types used in the policy. At run time, the latest deployed version of the policy will be used.  
  
5. In the **Specify policy parameters** list box, select a variable from the **Parameter Name** property.  
  
   > [!NOTE]
   >  The **Call Rules** shape is essentially reconstructing the message, as if using a **Construct** shape, which in turn may cause context properties of the message to be lost.  
  
   > [!NOTE]
   >  You can specify a message or a .NET variable as a parameter to a BRE policy. To pass a **TypedXmlDocument** fact, specify the corresponding message declared in the orchestration as a parameter. To pass a .NET fact, specify a .NET variable declared in the orchestration as a parameter. To pass a database fact, specify a .NET variable of type **DataConnection** or **TypedDataTable** as a parameter to the policy.