---
title: "Configuration Information | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Call Rules shape [Orchestration Designer], planning"
  - "Call Rules shape [Orchestration Designer], configuring"
ms.assetid: aa4924c6-4270-473b-aa0a-6d8b18375a39
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Information
This topic describes how to configure the **Call Rules** shape.  
  
## Orchestration variables and fact types  
 In the orchestration where the **Call Rules** shape resides, you must have variables that match types used in the policy. If you do not have the correct types of variables, you cannot supply the correct parameters to the policy. Suppose that you have a **Call Rules** shape in an orchestration, CallMyRules, and you use CallMyRules to call MyPolicy. If a .NET class, MyClass, is used in MyPolicy, you must create a variable of a MyAssembly.MyClass type in the orchestration. Similarly, if MyPolicy has **DataConnection** bindings, you must create a variable of a **Microsoft.RuleEngine.DataConnection** type in the orchestration.  
  
 In addition to creating the variables in the orchestration, you must also create instances for these variables. You can do this by adding an **Expression** shape to your orchestration. Using the preceding example, you should instantiate a MyAssembly.MyClass instance and a **DataConnection** instance. To instantiate the **DataConnection** instance, you do the following:  
  
-   Create a **SqlConnection** instance and assign it to MySqlCon.  
  
-   Create a **DataConnection** instance and assign it to dataConnection (variable of **DataConnection** type), as shown in the following code fragment:  
  
    ```  
    dataConnection = new Microsoft.RuleEngine.DataConnection("NameOfSqlDatabaseHere", "NameOfYourTableHere", MySqlCon);  
    ```  
  
> [!NOTE]
>  If you do not have variables matching the fact types, these types will not appear as parameters in the **Specify policy parameters** list box in the **CallRules policy configuration** dialog box.  
  
> [!NOTE]
>  The orchestration engine automatically converts the message variables you specify as parameters to a BRE policy into **TypedXmlDocument** objects, and asserts them into working memory of the rule engine prior to executing the policy. Therefore, you do not need to declare variables of type TypedXmlDocument as you did for .NET and database facts.  
  
## Message type and document type  
 You must ensure that the **DocumentType** property for XML nodes used in your business rule (that you implement in the Business Rule Composer) is the same as the **MessageType** for those XML nodes defined in the orchestration—it must match the **MessageType** of the message or message part that will be passed to the rule engine in the **Call Rules** shape.  
  
 For example, if you define a purchase order (PO) XML schema in a BizTalk project, the **MessageType** defined for this schema is **BTSProject.PO** (if **BTSProject** is the namespace or the project name using the default namespace).  
  
 In the case of the **PO\Amount** element, before you drop it into a rule definition, you must change its **DocumentType**property to **BTSProject.PO** in the properties window. You can access the properties window when any node in the schema is selected on the **XML Schemas** tab in the Facts Explorer. This change is applied for all elements in the schema, but is not persisted with the schema. It must be reset when the Business Rule Composer is launched or the schema is reloaded. This is required for vocabulary definitions based either on XML schemas or on rules built directly from XML schemas. If you do not do this, you can still execute the policy, but the **Call Rules** shape will not work correctly, and message type will not appear in the **Specify policy parameters** list box in the **CallRules policy configuration** dialog box.