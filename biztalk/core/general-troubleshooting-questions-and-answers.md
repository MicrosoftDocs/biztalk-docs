---
title: "General Troubleshooting Questions and Answers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2f89d92-0a97-4017-8b8e-6afd8b20eaf4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# General Troubleshooting Questions and Answers
This topic has questions and answers to help you resolve issues with the BizTalk Mapper.  
  
## How do I specify XSLT output settings?  
 You can use the BizTalk Mapper to include or omit XML declarations, and control the encoding used for output instance data.  
  
#### Include or exclude an XML declaration  
  
1.  In the Grid view, click the mapper grid. The **Properties** window displays the grid properties.  
  
2.  In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration, or select **No** not to omit an XML declaration.  
  
#### Set encoding for output instance data  
  
1.  In the Grid view, click the mapper grid. The **Properties** window displays the grid properties.  
  
2.  In the drop-down list for the **XSLT Encoding** property, select the character set you want to use for the output instance data.  
  
## How do I create multipart mappings?  
 If you have multiple maps that are used together, you will need to combine them in an orchestration by using the **Transform** shape to test them together. The BizTalk Mapper can test only one map at a time.  
  
## Why isn't my database functoid working?  
 The database functoids **Database Lookup** and **Value Extractor** do not directly return error information; rather, they capture the information and supply it to the **Error Return** functoid for use by your map. You can use the **Error Return** functoid for error detection as in the following scenarios:  
  
- When your map has a **Database Lookup** or **Value Extractor** functoid that is not behaving as expected. To see the error message, temporarily map the functoid to a field in the output schema.  
  
- If your application expects different message content when database operations fail. You can use the **Error Return** functoid to detect an error and map the error message to an alternate structure so that downstream applications can react in a controlled manner.  
  
  To avoid errors that are detected only at run time, make sure that the first parameter to the **Error Return** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the Database category.  
  
  For more information about using the **Error Return** functoid (including a sample), see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Why is my map failing when calling my custom functoid?  
 Custom functoids must be installed into the global assembly cache (GAC) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before they can be invoked by a map. Verify that the assembly containing your custom functoid has been signed and placed into the GAC. Also, copy the assembly into the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”.  
  
 For more information about installing assemblies to the GAC, see [Assembly Installation in the GAC](../core/assembly-installation-in-the-gac.md). To view assemblies installed in the GAC, navigate to the Assembly directory of your [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] installation directory.  
  
## See Also  
 [Troubleshooting Maps](../core/troubleshooting-maps.md)