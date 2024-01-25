---
description: "Learn more about: How to Resolve Map Warnings and Errors"
title: "How to Resolve Map Warnings and Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Resolve Map Warnings and Errors
When you compile a map, you may find that warnings and errors result from the compilation process.  
  
## Resolve warnings and errors when building a map  
  
1.  For link and functoid errors, in the **Error List** window, double-click any description.  
  
     The link, functoid, or the schema node associated with the error is highlighted. Resolve the issue.  
  
2.  Review the **Description** area in the **Error List** window to determine additional errors.  
  
3.  Click the **Output** window tab to view additional warning and error message information.  
  
4.  After you have resolved all issues, right-click the map file name in Solution Explorer, and then click **Test Map** or **Build Solution**, as the case may be.  
  
    > [!NOTE]
    >  If a warning appears, the problem might exist over several grid pages. For example, you have grid page 1 with a record (named **Item**) in the source schema tree linked to a record (named **Number**) in the destination schema tree. On grid page 2 you have a record (named **Product**) in the source schema tree linked to the same **Number** record in the destination schema tree. In this scenario, a warning message is generated stating that you have multiple inputs to the same record. However if you view grid page 1, you see only one input into the **Number** record. 
  
## See Also  
 [Compiling and Testing Maps](../core/compiling-and-testing-maps.md)   
 [BizTalk Mapper Errors](../core/biztalk-mapper-errors.md)   
 [Troubleshooting Maps](../core/troubleshooting-maps.md)
