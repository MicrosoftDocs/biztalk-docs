---
description: "Learn more about: Merging XML Documents"
title: "Merging XML Documents"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Merging XML Documents
One of the messages that the **OrderBroker** orchestration creates is one to update the SQL Server history database. This message contains fields from the order message as well as the original order message. The original order appears in this message a string. This matches the data type for the order history in the database.  
  
 It isn't possible to take a message, convert it to a string, and place it in another message with a map. The orchestration uses a helper function, **InsertOrderBody**, to add the original order message as a string to the base history message.  
  
 The **OrderBroker** orchestration uses the map, **CSR_OrderRequest_To_SQLHistoryInsert**, to convert the order message into the base history message. The information for an order appears as attributes of an **OrderLog** element. The original message appears as another attribute of this element.  
  
 The **InsertOrderBody** method takes as arguments the original order message, the base history message, and returns the completed history message. The following code shows the portions of the method that inserts the message as a string:  
  
```  
public static XmlDocument InsertOrderBody( XmlDocument orderDoc,   
                                    XmlDocument historyInsertDoc)  
{  
...  
    XmlNode root = historyInsertDoc.FirstChild;  
  
    //Create a new attribute.  
    XmlNode attr = historyInsertDoc.CreateNode(XmlNodeType.Attribute,  
                                     "OriginalMsg", root.NamespaceURI);  
    attr.Value = orderDoc.OuterXml;  
  
    try  
    {  
        // XPath expression not shown for formatting reasons and  
        // replaces ".." in the following code  
        XmlNode destnode = historyInsertDoc.SelectSingleNode("..");  
        //Add the attribute to the document.  
        destnode.Attributes.SetNamedItem(attr);  
    }  
...  
  
    return historyInsertDoc;  
}  
```  
  
 After verifying that it received both arguments, the **InsertOrderBody** method finds the root node of the history update message. It then creates a node containing the **OriginalMsg** attribute and assigns the original order message to the attribute's value. At this point, the node simply exists. It is not yet part of a element.  
  
 After creating the attribute node, the method finds the node where it will attach the attribute using an XPath expression. After it locates the node, the method adds the attribute node to the attributes collection of the node.  
  
> [!NOTE]
>  Although the **OriginalMsg** attribute does not initially exist in the base history message, it is, of course, specified in the schema. XML elements that you add to your messages in code should be specified in the schemas for those messages.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)
