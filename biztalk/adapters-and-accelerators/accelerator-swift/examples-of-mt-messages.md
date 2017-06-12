---
title: "Examples of MT Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 629042cc-b941-4c58-b0dd-ede056caf573
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Examples of MT Messages
**Commands to generate the solution (InfoPath form template) for the Different MT messages:**  
  
 The following examples require that the "SWIFT Base Types.xsd", "SWIFT Common Data Types.xsd","MT102.xsd", "MT500.xsd", and "MT103.xsd" schemas are all in c:\schemas. This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder. The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated. These examples assume that the utility has been placed in “C:\FormGeneratorUtility2008” folder. Replace the location that you have selected for the utility in the below commands.  
  
-   **To generate a form for the MT103 schema:**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103`  
  
-   **To generate a form for the MT103, MT102, and MT500 schema:**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas MT103 MT102 MT500`  
  
-   **To generate a form for the MT103 schema (from the file):**  
  
     `FormGenerator.exe -b “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f P1forms.txt`