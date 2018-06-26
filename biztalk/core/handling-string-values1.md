---
title: "Handling String Values1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "jdearglist.txt, configuring strings"
  - "strings, left-justified"
  - "strings, configuring"
  - "strings, right-justified"
ms.assetid: a180b818-1009-45f5-a503-d10ed7dd27fc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Handling String Values
This topic describes how to configure certain string arguments as right-justified (and left padded).  
  
## Types of String Values  
 JD Edwards OneWorld exposes two kinds of string values through its interoperability layer:  
  
- Char: a single character  
  
- maximum length string  
  
  JD Edwards OneWorld uses Hungarian notation to name the arguments of these types in the business functions. For example, arguments of these types begin with:  
  
- c  
  
- sz  
  
### Left-Justified Values  
 For a majority of sz-type arguments, maximum length string or char array, JD Edwards OneWorld expects a left-justified value. For a street address line, which is of maximum length 40, JD Edwards OneWorld expects (for example):  
  
 "4567 Main St.       "  
  
 padded to length 40 with blanks. It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards OneWorld provides this for you. You only need to enter "4567 Main St.", in your client code.  
  
### Right-Justified Values  
 For some subset of values for this type, JD Edwards OneWorld expects values that are right justified with padding on the left. For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12. This argument represents a plant, such as a production facility. For a plant number of 30, J.D. Edwards OneWorld XE expects a value of:  
  
 "          30"  
  
 To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt. The jdearglist.txt is read when you generate the schema. Any value that is listed in this text file is automatically converted to a right-justified value and padded on the left with blanks.  
  
 You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder: %BizTalk_Install_Adapter%\config\JDE\  
  
 Where **%BizTalk_Install_Adapter%** is the directory in which you installed BizTalk Adapter for JD Edwards OneWorld.  
  
 If this file does not exist or is empty, an informational message appears in the BizTalk Adapter for JD Edwards OneWorld log when the adapter first opens.  
  
> [!NOTE]
>  If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains.  
  
 To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.  
  
 The following is an example of the format for entries in the jdearglist.txt file:  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
```  
  
 For example:  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 For a set of business functions belonging to the same business module, like-named arguments (of the same type) are shared across some or all of the business functions. You can use the wildcard character (*) instead of the business function name. For example:  
  
```  
B4200310.*.szBusinessUnit  
```  
  
> [!NOTE]
>  When importing a JD Edwards OneWorld business process to another computer, you must copy jdearglist.txt manually.  
  
## See Also  
 [Setting String Justification in Jdearglist](../core/setting-string-justification-in-jdearglist.md)   
 [Appendix A: Data Types](../core/appendix-a-data-types.md)