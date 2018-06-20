---
title: "Child Order Considerations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4f7aa81-5c08-4932-9e28-31e22e037999
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Child Order Considerations

## Requirements for header in a flat file
There are two scenarios related to delimited flat files for which special considerations apply when setting the **Child Order** property. The first such scenario concerns situations in which the flat file document has a header, a body, and optionally, a trailer. In these scenarios, you must observe the following requirements:  

- You must set the **Child Order** property of the (delimited) root record of the header to **Postfix**.  

- If a trailer is present, you must set the **Child Order** property of the (delimited) root record of the body to **Postfix**.  

- If a trailer is not present, you may set the **Child Order** property of the (delimited) root record of the body to **Prefix**, **InFix**, or **Postfix**.  

- If a trailer is present, you may set the **Child Order** property of the (delimited) root record of that trailer to **Prefix**, **InFix**, or **Postfix**.  

- You may set the **Child Order** property of delimited subordinate records of the header, body, and trailer to **Prefix**, **InFix**, or **Postfix**.  

  The second scenario related to delimited flat files and the **Child Order** property is that this property must be set according to what the runtime components expect for the nodes. The correct setting for the **Child Order** property may not be apparent for root and group nodes, as illustrated in the following scenarios:  

- **Root node.** Consider a typical flat file whose structure consists of records followed by a CR/LF combination. The delimiter separates records in the file, and the sequence is typically record, delimiter, record, delimiter, and so on. In this situation, the delimiter always follows the data, which corresponds to a **Child Order** property setting of **Postfix**.  

- **Group nodes.** The group nodes shown in the BizTalk Server and XSD representation of the schema are not explicitly present in the flat file representation of the instance message. Consider a purchase order (PO) that contains a collection of records for each line item, and those records repeat numerous times to represent multiple line items in a single PO. The schema for such a message would likely include a node named LineItems to serve as the (sometimes conceptual) container for the repeating set: in the flat file representation of the instance message, the LineItems container is conceptual in nature, represented by the appropriate sequence of data and delimiters; in the XML representation of the instance message, the LineItems container is explicitly present in the form of a **LineItems** element in XML.  

  Consider a message containing a root node and only one group node. It is easy to see where the last delimiter in the input stream would belong to the root node. Therefore, the data/delimiter sequence in the conceptual loop would merely be one or more line item records. Only in the case where there are more than one line item records would there be a delimiter to separate them. In that case, the number of delimiters is one less than the sets of things being delimited, and the delimiters are located between the delimited items in a structure known as Infix.  

## See Also  
- [Delimited Record Considerations](../core/delimited-record-considerations.md)   
- **Child Order (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
