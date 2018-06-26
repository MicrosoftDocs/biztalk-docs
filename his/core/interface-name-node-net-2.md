---
title: "Interface Name Node (.NET)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15466"
ms.assetid: 86d967fc-162c-47c1-b608-4ad8057b1464
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Interface Name Node (.NET)
Use the ***interface name*** node to view the list of all the methods in a component.  
  
 Double-click the ***interface name*** node to expand it. The right pane displays the following information about the methods:  
  
- **Method Name**. The method name.  
  
- **Return Type**. The method return type.  
  
- **Host Data Type**. The COBOL or RPG equivalent of the method's return type.  
  
- **Array Sizes**. If the return type is an array, this column will contain the number of dimensions and their sizes. For example, a single dimension of size 10 will be displayed as (10); a 3-dimensions array with sizes 2, 4, and 6 will be displayed as (2, 4, 6).  
  
- **Rows**. The number of rows, if the return type of the array is a data table.  
  
- **Link-to-Program Name**. The name of an executable running under the host environment that will be linked to by this method and passed a COMMAREA. It is valid only for link models.  
  
- **TP Name**. The transaction program (TP) name used by the method to locate a program to be executed. In the case of link models, it identifies the mirror transaction identifier which parses the distributed program link (DPL) header and identifies the link-to-program name.  
  
- **Meta Data**. Indicates whether the host is sent no metadata, only the name of the method, or all metadata.  
  
  Right-click the ***interface name*** node to view the following seven options:  
  
- **Add Method**. Adds a new method with no return type.  
  
- **Paste**. Inserts the method from the Clipboard into the current interface definition.  
  
- **Properties**. Displays the **Properties** window.  
  
## See Also  
 [Interface Properties](../core/interface-properties2.md)   
 [Method Properties](../core/method-properties1.md)   
 [Method Name Node (.NET)](../core/method-name-node-net-2.md)   
 [.NET Framework Library Nodes](../core/net-framework-library-nodes2.md)