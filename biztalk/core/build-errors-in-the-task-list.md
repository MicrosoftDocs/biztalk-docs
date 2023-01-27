---
description: "Learn more about: Build Errors in the Task List"
title: "Build Errors in the Task List | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "building, errors"
  - "errors, building"
ms.assetid: 05b36511-3031-4e13-ac2f-bfdbec0f48cb
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Build Errors in the Task List
When you build your project, or solution, the results will appear in the Output window, while individual errors and warnings will appear in the task list.

 Errors and warnings appear in the task list. You can double-click the error, and the focus will be applied to the object that is not correctly configured.

> [!NOTE]
>  When you build, the compiler does not validate XPaths. Take care to use valid XPath syntax.

## Insufficient configuration Action
 ![Image that shows the icon that represents an insufficient configuration action.](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")

> [!CAUTION]
>  While Orchestration Designer will provide insufficient configuration warnings where it can, there is no guarantee that your orchestration will compile correctly in the absence of such warnings.

## Compiler asks if you are missing an assembly reference

### Problem
 When you compile your orchestration you get an error message that ends with the question "are you missing an assembly reference?" Two of the more common messages are:

-   The type or namespace name 'X' does not exist in the namespace 'Y' (are you missing an assembly reference?)

-   Identifier 'X' does not exist in 'Y'; are you missing an assembly reference?

### Cause
 Any of the following could be the cause of this error.

-   Your project does not reference one or more required assemblies.

-   Your project has a map or other object type that has the same name as the project.

-   Your project uses XML Schema definition language (XSD)-based Partner Interface Process (PIP) schemas and contains XSD schemas in a subfolder that is named System.

-   Your project is using a Global Property whose namespace is a subset of the current project's namespace. For example, using the Global Property namespace "File.ReceivedFileName" in an orchestration contained in the project "Accounts.FILE".

### Resolution
 Depending upon the cause of the problem, the resolution could be any of the following:

-   Add a reference to the missing assemblies your project requires.

-   Change the name of the map or other object to something other than the project name. This can typically be done through the object's property page (for example, the Map property page contains a Name property).

-   Change the namespace for the schemas in Visual Studio. To do this using Visual Studio, click **Show All Files** on the **Project** menu, and then expand the **System** node in Solution Explorer. Click each file in the System folder and in any subfolders, and then change the namespace entry in the Properties window so that any occurrence of **System** becomes _**System**. For example, change the **MyProject.System.SubFolder** namespace to **the MyProject._System.Subfolder** namespace. For more information about this issue, see KB article [916649](https://support.microsoft.com/?kbid=916649).

-   Remove the conflicting Global Property namespace from the project.

## You receive a "Message has not been initialized in construct statement" error when building your project

### Problem
 When you compile your BizTalk application, you get the error "Message has not been initialized in construct statement".

### Cause
 When you construct a message, you specify all the message variables. Then you make assignments to the message or its parts. If part of a specific message assignment is included in a separate **Construct Message** shape, you may receive the initialization error message.

### Resolution
 To resolve this behavior, make sure that you include all parts of a specific message assignment in the same **Construct Message** shape. For a related support issue, see KB article [870606](https://support.microsoft.com/?kbid=870606).

 You can also resolve this behavior by creating your message in a **Construct** shape before using an instance of it in an **Expression** shape. For example, the following code will cause an error if placed in an **Expression** shape:

```
XMLDOM = new System.Xml.XmlDocument();
POAckMsg = XMLDOM;
```

 To fix, create the instance of XMLDOM in a **Construct** shape, and then do the assignment in a downstream **Expression** shape.

## You receive a "use of unconstructed message" error when building your project

### Problem
 When you compile your BizTalk project, you receive the error "use of unconstructed message '\<message\>'".

### Cause
 This error occurs when an unconstructed message is used in a **Send** shape.

### Resolution
 To resolve this issue, add a **Construct Message** shape to the orchestration. Include the **Construct Message** shape before the **Send** shape that is bound to the Web service.

 For more information about this error and Web services, see KB article [921043](https://support.microsoft.com/?kbid=921043).

## Setting a transaction level for a scope results in an error

### Problem
 After configuring the transaction type for a scope or other entity supporting transactions in an orchestration, you receive the error "A Non-transactional Orchestration cannot contain any other Transactions".

### Cause
 This error occurs when you try to configure the transaction type of a scope (or other entity) in an orchestration to "Atomic" or "Long-Running" when the orchestration itself has a transaction type of "None".

### Resolution
 Ensure that the transaction type settings of your orchestration and constituent objects are compatible.

## Project build results in the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"

### Problem
 When you compile your BizTalk project, you receive the error "you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port".

### Cause
 This error can occur if your orchestration has no activating **Receive** shapes (Activate = true) or has no activating **Receive** shapes and is not called directly by another orchestration.

### Resolution
 If your orchestration is not called by another orchestration, you must configure one of the **Receive** shapes to be an activated receive. For more information about configuring the **Receive** shape, including links to correlation, see [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md).

## You receive the error "Assembly generation failed -- Referenced assembly '\<assembly\>' does not have a strong name" when building your solution

### Problem
 You receive the error "Assembly generation failed -- Referenced assembly '\<assembly\>' does not have a strong name" when building your solution that has an orchestration.

### Cause
 This problem occurs when a type from an unsigned referenced assembly is used within an orchestration.

### Resolution
 Apply a strong name to the referenced assembly. If it is a custom assembly that you can recompile, use the strong name tool to create an .snk (key) file and then reference that key file in the assembly properties for the project. For more information about strong naming an assembly, see [How to Configure a Strong Name Assembly Key File](../core/how-to-configure-a-strong-name-assembly-key-file.md).

## The error "Failed to add resource(s). Change requests failed for some resources" occurs when deploying an orchestration

### Problem
 When deploying an orchestration, an error similar to the following is displayed and deployment of the orchestration fails:

```
Failed to add resource(s). Change requests failed for some resources. BizTalkAssemblyResourceManager failed to complete end type change request. Object reference not set to an instance of an object.
```

### Cause
 This error can occur if the orchestration contains any objects that use C# keywords.

### Resolution
 Remove any C# keywords from the orchestration. For a list of C# keywords, see [here](/dotnet/csharp/language-reference/keywords/).

## You receive an "invalid property value" error when compiling your orchestration

### Problem
 You receive the error dialog "Invalid property value" when building your orchestration.

### Cause
 One or more of the objects in your solution has the same name as another object. For example, a message name is the same as a port name.

### Resolution
 Ensure that every object in your solution has a unique name. You can minimize the risk of this error by adhering to a naming convention.

## See Also
 [How to Build Orchestrations](../core/how-to-build-orchestrations.md)
