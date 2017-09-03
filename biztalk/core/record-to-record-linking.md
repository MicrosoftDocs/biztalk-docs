---
title: "Record-to-Record Linking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a3fa4d7-5689-4f55-af1b-369defa37037
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Record-to-Record Linking

## Overview
In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use BizTalk Mapper to create multiple links between similar portions of the source and destination schemas at the same time. In previous versions of BizTalk Server, you had to create such links individually, one at a time. There are two distinct types of record-to-record linking, each appropriate to different scenarios based on the degree of similarity of the structures of the source and destination schema records being linked, as follows:  
  
-   **Structure linking.** Use structure linking when the structure of the records being linked in your source and destination schemas are the same or very similar.  
  
-   **Name-matching linking.** Use name-matching linking when the structure of the records being linked in your source and destination schemas are still similar, and with matching record and field names, but with more structural exceptions than are workable with structure linking.  
  
    > [!NOTE]
    >  Record-to-record linking applies to value-copy linking only, as configured using the **Source Links** property.  
  
## Record-to-Record Linking: Structure Links  
 Use structure linking when the structure of the records that you want to link in your source and destination schemas is the same or almost exactly the same.  
  
 If the structure of your schemas is exactly the same, you need only add one link at the root node of each schema. In the shortcut menu, select the desired mode of linking.  
  
 If the structure of particular records in your schemas is exactly the same, you need only add one link between those records in each schema. In the shortcut menu, select the desired mode of linking.  
  
 For information about how to configure record-to-record linking as using either structure linking or name-matching linking, see [Link Records Automatically](../core/how-to-link-records-automatically.md).  
  
> [!NOTE]
>  Structure links are the default type of record-to-record linking.  
  
## Record-to-Record Linking: Name-Matching Links  
 Use name-matching links when the structure of the records that you want to link in your source and destination schemas is very similar, but not exactly the same. For example, the source or destination schema might have more subordinate records or fields within the nodes to be linked than in the other schema.  
  
 To create a name-matching link between portions of your source and destination schemas that have nearly matching structures, including the entire schemas where applicable, create a link originating from a sub-hierarchy parent node and ending on another sub-hierarchy parent node. In the shortcut menu, select the desired mode. After you link the nodes, links are automatically created for all of the subordinate records and fields in the source and destination schemas that are named the same and have the same substructure.  
  
 For information about how to configure record-to-record linking as using either structure linking or name-matching linking, see [Link Records Automatically](../core/how-to-link-records-automatically.md).  
  
## See Also  
 [Link Records Automatically](../core/how-to-link-records-automatically.md)   
 [Edit Link Properties](../core/how-to-edit-link-properties.md)