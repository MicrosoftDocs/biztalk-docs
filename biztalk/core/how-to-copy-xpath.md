---
title: "How to Copy XPath | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 404599d4-0fb3-4c7c-91e6-1295d9d0965e
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy XPath
The XML Schema definition (XSD) language provides the underlying syntax of the message schemas defined within BizTalk Server. Although the tree views in BizTalk Mapper use a BizTalk-specific graphical hierarchy of record and field nodes (among other types of nodes), each with its own set of properties, such hierarchies are constructed and persisted as XSD.  
  
 In scenarios where maps are complex and span across grid pages, locating the parent of a schema node can be difficult. The XSD path will be of use here. You can use the XSD path to get information about the depth of schema nodes. Also, you can reuse this path in another grid page to identify the relationship.  
  
## Prerequisites  
 These instructions require that BizTalk Mapper is running.  
  
### To copy the XSD path (XPath)  
  
1.  Right-click the schema node for which you want the XSD path, and then click **Copy XPath**.  
  
2.  Open a text editor. On the **Edit** menu, click **Paste**. You can now see the XSD path.  
  
    > [!NOTE]
    >  Alternatively, you can press CTRL+V to paste the path in a text editor.  
  
     The code below displays the XSD path for the selected schema node.  
  
    ```  
    /*[local-name()='<Schema>']/*[local-name()='Shipment']/*[local-name()='DataCollection']  
    ```  
  
## See Also  
 [Using Enhanced Features in BizTalk Mapper](../core/using-enhanced-features-in-biztalk-mapper.md)   
 [How to Replace Schemas](../core/how-to-replace-schemas.md)   
 [How to Expand and Collapse the Schema Trees](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)