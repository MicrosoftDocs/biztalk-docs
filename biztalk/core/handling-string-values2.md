---
title: "Handling String Values2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "string values, configuring"
  - "formatting strings"
  - "strings, formatting"
  - "left-justified string values"
  - "jdearglist.txt"
  - "strings, left-justified"
  - "right-justified string values"
  - "strings, right-justified"
ms.assetid: 23d54731-b2b9-4610-a533-e041237e0bb3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Handling String Values
This topic describes how to configure certain string arguments as right-justified (and left padded).  
  
## Types of String Values  
 JD Edwards EnterpriseOne exposes two kinds of string values through its interoperability layer:  
  
- char: a single character  
  
- maximum length string  
  
  JD Edwards EnterpriseOne uses Hungarian notation to name the arguments of these types in the business functions. For example, arguments of these types begin with:  
  
- c  
  
- sz  
  
### Left-Justified Values  
 For a majority of sz-type arguments, maximum length string or char array, JD Edwards EnterpriseOne expects a left-justified value. For examples, for a street address line, which is of maximum length 40, JD Edwards EnterpriseOne expects (for example):  
  
 "4567 Main St.    "  
  
 padded to length 40 with blanks. It is not necessary for you to enter the padding because Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides this for you. You only need to enter "4567 Main St ", in your client code.  
  
### Right-Justified Values  
 For some subset of values for this type, JD Edwards EnterpriseOne expects values that are right justified with padding on the left. For example, for business functions in the B4200310 source module, the argument szBusinessUnit is of length 12. This argument represents a plant, such as a production facility. For a plant number of 30, JD Edwards EnterpriseOne expects a value of:  
  
 "           30"  
  
 To enter a value that will be right-justified, you must enter the parameter in a file called jdearglist.txt. The jdearglist.txt is read when you generate the schema. Any value in this text file is automatically converted to a right-justified value and padded on the left with blanks.  
  
 You must create jdearglist.txt using a text editor, with entries describing these parameters, and save it in the following folder:  
  
 C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config  
  
 If this file does not exist or is empty, an informational message appears in BizTalk Adapter for JD Edwards EnterpriseOne log when the adapter first opens.  
  
> [!NOTE]
>  If you change this file after generating your schema, you must regenerate the schema to refresh the data it contains. To verify that you are using the latest information in this file, you can use the Task Manager to stop the browsingagent.exe process before regenerating your schema; however, this should not be necessary.  
  
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
>  When importing a JD Edwards EnterpriseOne business process to another computer, you must copy jdearglist.txt manually.  
  
## See Also  
 [Appendix B: Data Types](../core/appendix-b-data-types.md)