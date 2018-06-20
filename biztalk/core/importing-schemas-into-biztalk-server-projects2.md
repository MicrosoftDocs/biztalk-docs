---
title: "Import JD Edwards EnterpriseOne schemas into Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Schemas into BizTalk Server Projects
This section discusses browsing a JD Edwards EnterpriseOne server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.  
  
> [!NOTE]
>  You must ensure that you set the arglist. You must update jdearglist.txt before you generate the schemas in the orchestration. For more information, see [Handling String Values](../core/handling-string-values2.md).  
  
> [!NOTE]
>  Each time that you change the jdearglist, you must regenerate the schemas for that business object.  
  
 After creating the JD Edwards EnterpriseOne port, you can browse JD Edwards EnterpriseOne by launching the Microsoft Adapter Wizard from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.  
  
## Import schemas into Visual Studio
  
1. Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Right-click the name of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.  
  
3. Click **Add** to open the **Add Adapter Wizard**.  
  
4. On the **Select Adapter** page, select the name of the adapter for which you want to import schemas (for example, **JDEEnterpriseOne**).  
  
5. In the **SQL Server** box, select a SQL server.  
  
6. In the **Database** box, select a database.  
  
    The default database is the same one as your SQL server.  
  
7. In the **Port** box, select a SQL server, and then click **Next**.  
  
    The JD Edwards EnterpriseOne system displays in the browser.  
  
8. Continue with the next procedure below.  
  
   The Add Adapter Wizard displays a tree of all of the defined systems. JD Edwards EnterpriseOne has many modules. The modules are grouped together according to the first three characters of their name.  
  
- The first level of the hierarchy is the list of all three-character prefixes for the module names.  
  
- The second level lists all the modules that share the same three-character prefix.  
  
- The last level lists the business functions belonging to a module. When you expand the services icon, you can view its operations.  
  
  Expanding an operation displays the input/output arguments. You can expand the input/output arguments to view the data types of the arguments.  
  
> [!NOTE]
>  If the server object definitions change, you must regenerate the schema to refresh the data it contains.  
  
> [!NOTE]
>  If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains. For more information on jdearglist.txt, see [Handling String Values](../core/handling-string-values2.md).  
  
## Select the schemas  
  
1. In the **Select Services to Import** page, expand the top level node of the **Business Objects** node or the **Business Services** node.  
  
2. Select the check box next to the items that you want to import, and then click **OK**.  
  
3. Schemas generated for the selected JD Edwards EnterpriseOne items are imported into your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.  
  
> [!NOTE]
>  When using AddressBook (N0100041) the field name is **cActionCode**. The action is part of the XML file itself. The codes are:  
  
-   A for Add  
  
-   C for Change  
  
-   D for Delete  
  
-   I for Inquiry  
  
## Next step
[Use Message Context Properties](../core/using-message-context-properties1.md)