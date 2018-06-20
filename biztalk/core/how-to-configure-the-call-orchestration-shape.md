---
title: "How to Configure the Call Orchestration Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Call Orchestration shape [Orchestration Designer], parameters"
  - "Call Orchestration shape [Orchestration Designer], configuring"
  - "Call Orchestration shape [Orchestration Designer], about Call Orchestration shapes"
  - "configuring [Orchestration Designer], Call Orchestration shapes"
  - "Call Orchestration shape [Orchestration Designer]"
  - "nonserializable objects"
  - "orchestrations, nonserializable objects"
  - "Call Orchestration shape [Orchestration Designer], referencing orchestrations"
  - "orchestrations, parameters"
ms.assetid: 718ce2a0-ac08-4662-8b4e-1be279dbc749
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Call Orchestration Shape
The **Call Orchestration** shape can be used to synchronously call an orchestration that is referenced in another project. This allows for reuse of common orchestration workflow patterns across BizTalk projects. When you invoke another nested orchestration synchronously with the **Call Orchestration** shape the enclosing orchestration waits for the nested orchestration to finish before continuing.  
  
 You can specify parameters that will be passed to the nested orchestration. Parameters can be messages, variables, port references, role links, or correlation sets. Passed-in port references, role links, and correlation sets all perform like self-addressed envelopes: they supply the nested orchestration information it can use to send information back to the enclosing orchestration.  
  
> [!CAUTION]
>  If you pass nonserializable objects such as XmlDocument or XmlNode as parameters to an orchestration, it will fail.  
  
 For an example of how to use **Call Orchestration** shape, see [CallOrchestration (BizTalk Server Sample)](../core/callorchestration-biztalk-server-sample.md).  
  
### To configure a Call Orchestration shape  
  
1. Using the **Orchestration Selection** drop-down list box, select an orchestration from the list.  
  
2. Using the **Orchestration Parameters** grid control, specify arguments to pass to the orchestration—as specified in the **Orchestration Selection** drop-down list box—that is called. You specify these arguments in the cells of the Variable column, one variable per cell, by typing the name of a variable or clicking a variable from a drop-down list in a cell.  
  
3. To configure the **Call Orchestration** shape according to the service and arguments that you specified in the dialog box, click **OK**. To close the **Call Orchestration Configuration** dialog box without making any changes to the **Call Orchestration** shape, click **Cancel**.  
  
   > [!CAUTION]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support recursive orchestrations. If Orchestration A calls or starts Orchestration B, then Orchestration B cannot call or start Orchestration A directly, nor can it call or start any orchestration that directly or indirectly calls Orchestration A.  
  
## Referenced Orchestrations  
 For the referenced orchestration to be callable, ensure that the following properties have been configured for the called orchestration:  
  
- Set the **Type Modifier** property to **Public** for the called orchestration. To set the **Type Modifier** property for an orchestration to **Public**, open the orchestration in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], click the green start shape at the top of the orchestration to display the **Orchestration Properties** dialog and set the **Type Modifier** property to **Public**.  
  
- Set the **Activate** property of the initial receive shape in the orchestration to **False**.  
  
## Orchestration Selection drop-down list box  
 Click the Down arrow in the drop-down list box to view available services and select one. This list contains all the services that can be called from the current orchestration, including referenced assemblies.  
  
## Orchestration Parameters grid control  
 You specify the arguments to pass to a parameterized orchestration by using the **Orchestration Parameters** grid control. The grid has four columns: Variables in Scope, Parameter Name, Parameter Type, and Parameter Direction. You can make changes only in the first column; the other columns are read-only.  
  
 When you select a valid orchestration, its parameters populate the parameter name, type and direction columns of the grid control. You then select the variables in each row to pass as arguments. You select these variables from a drop-down list present in each cell in the Variables in Scope column. This list displays all the available variables of the type specified in the adjacent Parameter Type cell. If only one object of that type is available, the Variables in Scope cell is automatically populated with that object. You can also type in a Variables in Scope cell to select a variable that is available in the drop-down list.  
  
> [!NOTE]
>  Because a **Call Orchestration** shape calls an orchestration, the "Orchestration Parameters" you select in this dialog box actually refer to orchestration variables.  
  
 If an orchestration you are calling has no defined parameters, the grid control in this dialog box is unavailable.  
  
## See Also  
 [How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md)