---
description: "Learn more about: Error Messages"
title: "Error Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "error messages, JD Edwards OneWorld adapters"
  - "adapters [JD Edwards OneWorld adapters], error messages"
  - "JD Edwards OneWorld adapters, error messages"
ms.assetid: 9fb65d50-83c6-426e-a0d6-674800ecf70f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error Messages for the JD Edwards OneWorld System
The following table describes error messages in the JD Edwards OneWorld system, and provides possible corrections for them.  
  
|Error ID|Possible Cause / Error Description|Possible Correction|  
|--------------|-----------------------------------------|-------------------------|  
|**E-JDE0002**|JD Edwards OneWorld JAR files missing.<br /><br /> Failed to instantiate class object for JD Edwards OneWorld Java Data Bean.|Verify path for repository.<br /><br /> For more information, see [Basic Types](../core/basic-types1.md).|  
|**E-JDE0027**|JD Edwards OneWorld JAR files missing. Unable to acquire JD Edwards OneWorld connection object.|Verify your CLASSPATH environment variable.<br /><br /> See Updating the CLASSPATH.<br /><br /> Verify your credentials.<br /><br /> For more information, see [Basic Types](../core/basic-types1.md).|  
||JD Edwards OneWorld JAR files missing.<br /><br /> Wrong path for repository.|Verify location of jdeinterop.ini. Verify path for repository set in the jdeinterop.ini file.<br /><br /> You must copy jdeinterop.ini manually when importing a JD Edwards OneWorld  business process to another computer.|  
||Unable to acquire JD Edwards OneWorld connection object.|Verify your CLASSPATH settings and logon credentials..|  
|**I-JDE0043**|Wrong App Server, Port, Environment, Path for Configuration File, User, Password.<br /><br /> Logon failed.|Verify your logon credentials.<br /><br /> For more information, see [Basic Types](../core/basic-types1.md).|  
|**I-JDE0048**|If the jdearglist.txt file does not exist or is empty, an informational message appears in the log when Microsoft BizTalk Adapter for JD Edwards OneWorld opens.|Update the jdearglist.txt file to enter a list of parameters so that they are automatically right justified and padded on the left with blanks.<br /><br /> See [Handling String Values](../core/handling-string-values1.md).<br /><br /> Every time you change the jdearglist, you must regenerate the schemas for that business object.|  
  
## See Also  
 [Appendix A: Data Types](../core/appendix-a-data-types.md)   
 [Troubleshooting JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)
