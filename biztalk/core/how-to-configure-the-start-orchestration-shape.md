---
title: "How to Configure the Start Orchestration Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [Orchestration Designer], Start Orchestration shapes"
  - "Start Orchestration shape [Orchestration Designer], parameters"
  - "Start Orchestration shape [Orchestration Designer], configuring"
  - "orchestrations, starting"
  - "Start Orchestration shape [Orchestration Designer]"
  - "Start Orchestration shape [Orchestration Designer], starting orchestrations"
  - "Start Orchestration shape [Orchestration Designer], about Star Orchestration shape"
ms.assetid: 9d01c41e-9bc5-4c1c-a869-b2f0df13036a
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Start Orchestration Shape
The **Start Orchestration** shape is similar to the **Call Orchestration** shape, but you invoke another orchestration asynchronously with the **Start Orchestration** shape—that is, the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.  
  
 You can specify parameters that will be passed to the invoked orchestration. Parameters can be messages, variables, port references, role links, or correlation sets. The **Start Orchestration** shape can only take *in* parameters; it cannot take *out* or *ref* parameters.  
  
> [!CAUTION]
>  If you pass non-serializable objects such as XmlDocument or XmlNode as parameters to an orchestration, it will fail.  
  
 The **Start Orchestration** shape is the only shape in which you can reverse the polarity on a port being passed as a parameter—for example a *uses* port (send port) can be passed in to an invoked orchestration, but the invoked orchestration can treat it as an *implements* port (receive port). Note that this can only be done with ports that use direct binding.  
  
 The **Start Orchestration** shape can also be used to call an orchestration that is referenced in another project. This allows for reuse of common orchestration workflow patterns across BizTalk projects. For the referenced orchestration to be callable, ensure that the **Type Modifier** property for the called orchestration is set to **Public**. To set the **Type Modifier** property for an orchestration to **Public**, open the orchestration in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], click the green start shape at the top of the orchestration to display the **Orchestration Properties** dialog and set the **Type Modifier** property to **Public**. The default value for **Type Modifier** is **Private**.  
  
 For an example of how to use **Start Orchestration** shape, download the SDK sample "Implementing Scatter and Gather Pattern" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
### To configure a Start Orchestration shape  
  
1. Using the **Orchestration Selection** drop-down list box, select an orchestration from the list.  
  
2. Using the **Orchestration Parameters** grid control, specify arguments to pass to the orchestration—as specified in the **Orchestration Selection** drop-down list box—that is started. You specify these arguments in the cells of the Variable column, one variable per cell, by typing the name of a variable or clicking a variable from a drop-down list in a cell.  
  
3. To configure the **Start Orchestration** shape according to the service and arguments that you specified in the dialog box, click **OK**. To close the **Start Orchestration Configuration** dialog box without making any changes to the **Start Orchestration** shape, click **Cancel**.  
  
   > [!CAUTION]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support recursive orchestrations. If Orchestration A calls or starts Orchestration B, then Orchestration B cannot call or start Orchestration A directly, nor can it call or start any orchestration that directly or indirectly calls Orchestration A.  
  
## Orchestration Selection drop-down list box  
 Click the Down arrow in the drop-down list box to view available orchestrations and select one. This list contains all the orchestrations that can be started from the current orchestration, including referenced assemblies.  
  
## Orchestration Parameters grid control  
 You specify the arguments to pass to a parameterized orchestration by using the **Orchestration Parameters** grid control. The grid has four columns: Variables in Scope, Parameter Name, Parameter Type, and Parameter Direction. You can make changes only in the first column; the other columns are read-only.  
  
 When you select a valid orchestration, its parameters populate the parameter name, type, and direction columns of the grid control. You then select the variables in each row to pass as arguments. You select these variables from a drop-down list present in each cell in the Variables in Scope column. This list displays all the available variables of the type specified in the adjacent Parameter Type cell. If only one object of that type is available, the Variables in Scope cell is automatically populated with that object. You can also type in a Variables in Scope cell to select a variable that is available in the drop-down list.  
  
> [!NOTE]
>  Because a **Start Orchestration** shape starts an orchestration, the "Orchestration Parameters" you select in this dialog box actually refer to orchestration variables.  
  
 If an orchestration you are executing has no defined parameters, the grid control in this dialog box is unavailable.  
  
## In This Section  
 [How to Create Receive Subscriptions at Invoked Orchestrations](../core/how-to-create-receive-subscriptions-at-invoked-orchestrations.md) 
  
## See Also  
 [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md)