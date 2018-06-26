---
title: "How to Use Multi-part Message Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multi-part message types, parts"
  - "multi-part message types, creating"
  - "multi-part message types, type modifiers"
  - "messages"
  - "multi-part message types, deleting"
  - "orchestrations, messages"
  - "deleting, multi-part messages"
  - "multi-part message types, about multi-part message types"
  - "orchestrations, type modifier"
  - "messages, multi-parts"
  - "creating, multi-part messages"
  - "messages, about messages"
ms.assetid: 009a39bd-cfc4-42d9-918c-88ac24bfc370
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use Multi-part Message Types
Each message has a multi-part message type, a description of the message structure that consists of zero or more message parts. The parts are defined by XML Schema Definition (XSD) language schemas or .NET classes. You can define your own multi-part message types, or you can use existing .NET classes and schemas.  

 You can access or assign message parts directly within your orchestration, or you can use individual elements of message parts that are exposed as distinguished fields or property fields. For more information, see [Using Distinguished Fields and Message Properties](../core/using-distinguished-fields-and-property-fields.md).  

> [!NOTE]
>  A multi-part message type does not necessarily contain multiple parts.  

> [!NOTE]
>  A message part can be defined by the .NET type **XmlDocument**, which can be used to contain an arbitrary XML document, by any .NET type that is XML-serializable, or by any .NET type supporting custom serialization.  

## Add a multi-part message type  

1.  In the **Orchestration View** window, expand the **Types** node.  

2.  Right-click **Multi-part Message Types** and then click **New Multi-part Message Type**.  

     The **Multi-part Message Types** folder expands, if collapsed, and a new multi-part message type is added with one default message part.  

3.  Name the multi-part message type and the provided message part.  

     If your multi-part message type requires more than one message part, you can add additional parts by assigning a name to the \<New\> message part.  

4.  Associate each message part with a type, such as a .NET class or schema.  

## Remove a multi-part message type  

-   In the **Orchestration View** window, right-click the multi-part message type you want to remove and then click **Delete**.  

    > [!NOTE]
    >  Removing a multi-part message type from your orchestration will also remove the type information from messages that use it.  

    > [!NOTE]
    >  Items that appear as read-only are defined in another orchestration.  

## Remove a part from a multi-part message type  

-   In the **Orchestration View** window, right-click the part you want to remove and click **Delete**.  

    > [!NOTE]
    >  You cannot delete a message type's message part if the **Message Body Part** property is set to true. You must first set the **Message Body Part** property to True for another of the message type's parts.  

## Set the type modifier for a multi-part message type  

- In the **Properties** window, set the following property:  


  |     Property      |                                                                                                                                                                                        Description                                                                                                                                                                                         |
  |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | **Type Modifier** | Determines the scope of the multi-part message type:<br /><br /> -   <strong>Private—</strong>Access to this multi-part message type is limited to the containing module.<br />-   <strong>Public—</strong>Access to this multi-part message type is not limited.<br />-   <strong>Internal—</strong>Access to this multi-part message type is limited to modules within the same project. |

## Add parts to an existing multi-part message  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the ability to add parts to a multi part XLANG message and also to refer to a message part by an index greater than the originally declared number of parts if the part exists. This functionality may be useful for sending or receiving SMTP messages with a variable number of attachments. This functionality is implemented as follows:  

- From your project, add a reference to **Microsoft.XLANGs.BaseTypes**.  

- Create a variable (for example *xlangPart*) of type **Microsoft.XLANGs.BaseTypes.XLANGMessage**.  

- Call <em>xlangPart</em>**.AddPart(…)** using the appropriate arguments from an Expression shape.  

  > [!NOTE]
  >  The added parts are of type **XmlDocument** so you cannot add a custom formatted message part using the **AddPart()** method.  

> [!NOTE]
>  If a multi part message that contains greater than the number of declared parts is received, the orchestration engine reads how many parts there are in the message, then constructs the proper part types for the parts that match the number of parts in the declared message type and then constructs **XmlDocument** parts for the remaining parts.  

## See Also  
 **IBaseMessage.AddPart Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
 [XSD Resources on the Web](../core/xsd-resources-on-the-web.md)   
 [Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md)   
 [Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md)