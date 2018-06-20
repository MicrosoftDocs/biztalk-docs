---
title: "Debugging Orchestrations by using Custom Code | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, debugging"
  - "building, debugging"
ms.assetid: 94e569fa-8dea-4027-abb5-37b4a8015621
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Debugging Orchestrations by using Custom Code
If your orchestration is going to be exercised in a test environment or you are creating a prototype and want to modify the values of message fields and orchestration variables, you can write the output to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] console by using the following code in an **Expression** shape:  
  
```  
System.Diagnostics.Debug.WriteLine(iResult);  
```  
  
 You need to place this **Expression** shape immediately after the shape that performs the operation so that you can output the result for debugging.  
  
 Alternatively, you can write a simple custom debugger by creating a debugging DLL with a class that includes a method which takes as input a message with a format defined in your orchestration and referenced in the debug DLL. For more information about passing a message as a parameter, see [How to Use Expressions to Create Objects and Call Object Methods](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md).  
  
 This method can bring up a debug dialog that includes a combo box or other control to allow user modification of values, puts the edited message back together, and passes it back out as the return value.  
  
 Set up a Boolean variable to indicate whether or not your orchestration is in debug mode, then wherever you have a point in your orchestration at which you would like to be able to modify values, you can add a **Decide** shape with one live branch that runs only when your debug mode variable is set to True, or when a particular condition arises that you want to examine. You call your method from an **Expression** shape in the live branch of the **Decide**. When you no longer need to debug, you set your debug mode variable to False, or remove the **Decide** shape(s) altogether and recompile.  
  
## To Debug a .NET component called by an Orchestration  
 The following steps demonstrate how to debug a .NET component called by an Orchestration:  
  
1. Open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for your component.  
  
2. Set a breakpoint in your component on the method that is called by the orchestration.  
  
3. Click the **Debug** menu and select **Attach to Process…** to display the **Attach to Process** dialog.  
  
4. Click the **Select…** button next to the **Attach to:** text box to display the **Select Code Type** dialog.  
  
5. Click to select the option to **Debug these code types:** and select **Managed** and then click the **OK** button.  
  
6. Click to select the **BTSNTSvc.exe** process from **Available Processes** and then click the **Attach** button.  
  
7. Send a message to your orchestration through a receive port.  
  
8. The .NET component should be stopped in the breakpoint.  
  
9. You can perform debugging as usual with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  For best results, the .NET component should be registered in the Global Assembly Cache (GAC).  
  
## See Also  
 [Orchestration Debugger User Interface](../core/orchestration-debugger-user-interface.md)   
 [Debugging Orchestrations](../core/debugging-orchestrations.md)