---
description: "Learn more about: How to Add Orchestration Variables"
title: "How to Add Orchestration Variables"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add Orchestration Variables
The Orchestration View window enables you to manage an orchestration's properties (also known as **Service** properties), parameters, ports, messages, and other variables. In addition to ports and messages, you can create integer variables, Boolean variables, string variables, or variables of a .NET class.  
  
 You can also use the Orchestration View window to manage the variables that belong to your scopes.  
  
### To add a variable  
  
1.  In the Orchestration View window, right-click the **Variables** folder and then click **New Variable**.  
  
     The **Variables** folder expands, if collapsed, and a new variable is added.  
  
2.  Name the variable by typing a name in the Identifier property in the Properties window.  
  
3.  Associate the variable with a type, such as a .NET class.  
  
    > [!NOTE]
    >  The **Types** drop-down list contains the following predefined variable types: **boolean**, **byte**, **datetime**, **decimal**, **double**, **int16**, **int32**, **int64**, **sbyte**, **single**, **string**, **timespan**, **uint16**, **uint32**, and **uint64**. You can also access .NET data types and classes by selecting **\<.NET Class...\>**, which brings up the **Select Artifact Type** dialog box.  
  
4.  If you select a predefined variable type, you have the option of specifying an initial value for the variable. In the Properties window, set the **Initial Value** property.  
  
     Otherwise, if the selected type is a .NET class, you have the option of using a default constructor. In the Properties window, set the following property:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |**Use Default Constructor**|If a default constructor is available for a .NET class, this property determines whether the default constructor will be called when you use the variable for the first time:<br /><br /> True—The default constructor will be called. This is the default value when a default constructor is available.<br /><br /> False—The default constructor will not be called; you must call a constructor in an expression or make an assignment to the variable before you can use it in your orchestration.|  
  
    > [!NOTE]
    >  If the default constructor requires input parameters, you can set **Use Default Constructor** to **False** and then call the constructor from an **Assignment** shape; for example, `myVariable = myNamespace.myClass (param1, param2)`.  
  
    > [!NOTE]
    >  When you add a variable to the orchestration, before it is fully defined, you will see exclamation marks in the orchestration. If you delete this variable before it is fully defined and the exclamation marks still appear in the orchestration, you can force the orchestration to remove these exclamation marks by creating and then deleting an orchestration parameter.  
  
### To remove a variable  
  
-   In the Orchestration View window, right-click the variable you want to remove and then click **Delete**.
