---
title: "Validating a Map (EDI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: caf58ecf-ed10-4c13-8d7d-e007b9158b0e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating a Map (EDI)
You can validate a map at design time. To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment. This operation generates a file containing the underlying XSLT of the map and a file containing extension objects.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To validate a map  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project. To the project in Solution Explorer, add the map that you want to validate and its input and output message schemas.  
  
   > [!NOTE]
   >  The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder. For more information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).  
   > 
   > [!NOTE]
   >  You do not have to build the project to validate a map.  
  
2. Right-click the map in Solution Explorer, and then click **Validate Map**.  
  
3. Verify that there is a message in the Output window indicating that the operation succeeded.  
  
4. Note any warnings that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has posted in the **Output** window.  
  
5. In the **Output** window, note the name and path of the output XSLT. This XSL file will be given the same name as the map file, but with an XSL extension. You can press CTRL and click the link to display the XSL file in the BizTalk Editor.  
  
6. In the **Output** window, note the name and path of the extension object XML. You can press CTRL and click the link to display the XSL file in the BizTalk Editor.  
  
## See Also  
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)