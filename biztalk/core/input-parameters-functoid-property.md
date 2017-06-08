---
title: "Input Parameters (Functoid Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Input Parameters [functoids]"
  - "Input Parameters [functoids], about Input Parameters"
  - "functoids, parameters"
  - "constant input parameters [functoids]"
  - "link input parameters [functoids]"
  - "Input Parameters [functoids], constant input parameters"
  - "Input Parameters [functoids], link input parameters"
ms.assetid: e7af7273-1d80-4c6e-bb3e-0091700d35db
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Input Parameters (Functoid Property)
Use the **Input Parameters** property to open the **Configure \<Functoid> Functoid** dialog box, in which you can configure input parameters for the functoid, including changing the order of the input parameters when necessary, and creating constant input parameters to supplement the link input parameters.  
  
## Category  
 General  
  
## Value  
 The value of this property is an ordered list of input parameters for the selected functoid. These input parameters are of two types:  
  
-   **Link input parameters.** Link input parameters are the set of links attached to the left side of the selected functoid in a grid page, if any. These input parameters are created by dragging between the selected functoid and either a node in the source schema or another functoid located to the left of the selected functoid in the same grid page. Link input parameters that have been given a **Label** property value are shown in the input parameters list using that value; otherwise, the value of the **Link Source** property is shown (generally, the former is friendlier than the latter).  
  
-   **Constant input parameters.** Constant input parameters are constant values that are created within the **Configure \<Functoid> Functoid** dialog box by using the **Insert New Constant Input Parameter** button  
  
     ![Adding constant input parameters to a functoid](../core/media/add-input-parameters.gif "Add_input_parameters")  
  
     . Clicking this button inserts a new constant input parameter and provides an in-place edit box in which you can type its value. Thereafter, it is shown in the input parameters list using this value.  
  
 The order of input parameters is important to proper functoid operation, and you must use the **Configure \<Functoid> Functoid** dialog box to examine and change this order when necessary. Link input parameters are initially ordered by the order in which they are created, and constant input parameters are initially added to the end of the input parameter list. Use the **Move Selected Input Parameter Up**![Move up in the list](../core/media/move-up-button.gif "Move_up_button") and the Move Selected Input Parameter Down ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") buttons to change the order of the input parameters. For information about the proper order of input parameters to the various functoids, see [Functoid Reference](../core/functoid-reference.md).  
  
## Remarks  
  
 To undo a set of changes made in this dialog box, click **Cancel** to close the dialog box without saving changes, and then reopen it.  
  
 For more information about how this property is used to establish the correct set of input parameters to a functoid, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).  
  
## See Also  
 [General Functoid Properties](../core/general-functoid-properties.md)