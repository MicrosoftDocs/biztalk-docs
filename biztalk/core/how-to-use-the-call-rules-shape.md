---
description: "Learn more about: How to Use the Call Rules Shape"
title: "How to Use the Call Rules Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use the Call Rules Shape
In Orchestration Designer, you can use the **Call Rules** shape to call a business policy.  
  
## Configure the Call Rules shape  
  
1. From the Toolbox, in the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line on the Orchestration Design Surface.  
  
    —Or—  
  
    Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape** on the context menu, and then click **Call Rules**.  
  
   > [!NOTE]
   >  The **Call Rules** shape can be used outside of an atomic scope. 
   >
   > On older BizTalk Server versions, when inserting the **Call Rules** shape outside of an atomic scope, drag the shape from the toolbox to the orchestration design area. There is a limitation that causes the Insert Shape context menu to disable the Call Rules menu item when accessed outside of an atomic scope. 
  
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
