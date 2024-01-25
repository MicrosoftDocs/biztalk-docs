---
description: "Learn more about: Examples of MX Messages"
title: "Examples of MX Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Examples of MX Messages
Command Lines to generate the solution (InfoPath form template) for the Different MX messages  
  
 The following examples require that the “pacs.004.001.01" and “pain.002.001.01” schemas are all in c:\schemas. This will generate the solution for InfoPath Form Template in the "C:\GeneratedForms" folder. The folder name of the solution would be same as the name of the message for which the InfoPath form needs to be generated. These examples assume that the utility has been placed in “C:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\FormGeneratorUtility” folder. Replace the location that you have selected for the utility in the below commands.  
  
-   **To generate a form for the pacs.004.001.01 schema:**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01`  
  
-   **To generate a form for the pacs.004.001.01 and pain.002.001.01 schema:**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\MXTemplates” “C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas pacs.004.001.01 pain.002.001.01`
