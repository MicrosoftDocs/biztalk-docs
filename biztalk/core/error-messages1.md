---
description: "Learn about the error messages in the JD Edwards EnterpriseOne system and the possible corrections for the errors that they indicate."
title: "Error Messages1"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error Messages in the JD Edwards EnterpriseOne System

The following table describes error messages in the JD Edwards EnterpriseOne system and provides possible corrections for them.  
  
|Error ID|Possible Cause / Error Description|Possible Correction|  
|--------------|-----------------------------------------|-------------------------|  
|E-JDE0027|JD Edwards EnterpriseOne JAR files missing. Unable to acquire JD Edwards EnterpriseOne connection object.|Verify your credentials. Verify your CLASSPATH settings and logon credentials. Refer to Environment variable.|  
|I-JDE0043|Wrong App Server, Port, Environment, Path for Configuration File, User, Password. Log in failed.|Verify your log in credentials. Refer to Environment variable.|  
|I-JDE0048|If the jdearglist.txt file does not exist or is empty, an informational message appears in the log when Microsoft BizTalk Adapter for JD Edwards EnterpriseOne opens.|Update the jdearglist.txt file to enter a list of parameters so that they are automatically right justified and padded on the left with blanks. For more information, see  [Handling String Values](../core/handling-string-values2.md). Every time you change the jdearglist, you must regenerate the schemas for that business object.|  
|E-JDE0027|Unable to acquire JD Edwards EnterpriseOne connection object. Please check your CLASSPATH and credentials.|Verify the location of jdeinterop.ini.|  
  
## See Also  
 [Troubleshooting JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)   
 [Technical Reference](../core/technical-reference6.md)
