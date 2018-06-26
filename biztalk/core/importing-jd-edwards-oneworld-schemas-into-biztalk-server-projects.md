---
title: "Importing JD Edwards OneWorld Schemas into BizTalk Server Projects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "generating schemas"
  - "importing schemas"
  - "schemas, generating"
  - "schemas, importing into BizTalk Server projects"
ms.assetid: 5bcaa276-8c76-4212-b373-de86e3008a69
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing JD Edwards OneWorld Schemas into BizTalk Server Projects
This topic discusses browsing a JD Edwards OneWorld server and importing the schemas into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.  
  
> [!NOTE]
>  You must ensure that you set the arglist. You must update the jdearglist.txt before you generate the schemas in the orchestration. For more information, see [Handling String Values](../core/handling-string-values1.md).  
  
> [!NOTE]
>  Each time that you change the jdearglist, you must regenerate the schemas for that business object.  
  
 After creating the JD Edwards OneWorld logical system, you can browse JD Edwards OneWorld by opening the Microsoft Adapter Wizard from a BizTalk Server project.  
  
### To import schemas  
  
1. Open [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2. Right-click the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, point to **Add**, and select **Add Generated Items**.  
  
3. Click **Add adapter**, and select **Open**.  
  
4. Select the adapter, and click **Next**.  
  
    The JD. Edwards OneWorld XE system appears in the browser.  
  
    ![](../core/media/jdedadapter-04-jdebrowse.gif "JDEdAdapter_04_JDEBrowse")  
  
    The Adapter Wizard displays a tree of all of the defined systems. JD Edwards OneWorld has too many modules to show in one long list. The modules are grouped together according to the first three characters of their name.  
  
   - The first level of the hierarchy is the list of all three-character prefixes for the module names.  
  
   - The second level lists all the modules that share the same three-character prefix.  
  
   - The last level lists the business functions belonging to a module. When you expand the services icon you can view its operations.  
  
     Expanding an operation displays the input/output arguments.  
  
     You can expand the input/output arguments to view the data types of the arguments.  
  
   > [!NOTE]
   >  If the server object definitions change, you must regenerate the schema to refresh the data it contains.  
  
   > [!NOTE]
   >  If you change jdearglist.txt after generating your schema, you must regenerate the schema to refresh the data it contains. For information on jdearglist.txt, see to [Handling String Values](../core/handling-string-values1.md).  
  
## Generating Schemas  
 Use the following procedure to generate schemas.  
  
#### To generate schemas  
  
1.  Select the item for which you want to import schemas.  
  
2.  Click (or drag) to add the item to the **Transmit** pane (for an inbound to J. Edwards OneWorld call).  
  
3.  Click **OK**.  
  
     Schemas generated for the selected JD Edwards OneWorld item are imported into the BizTalk Server project.  
  
> [!NOTE]
>  When using AddressBook (N0100041) the field name is **cActionCode**. The action is part of the XML file itself. The codes are:  
>   
>  --A for Add  
>   
>  --C for Change  
>   
>  --D for Delete  
>   
>  --I for Inquiry  
  
## See Also  
 [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)