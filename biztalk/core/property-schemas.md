---
title: "Property Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8018bb72-a037-4eeb-bbbe-dd0cc6209aec
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Property Schemas

## Promoted properties
In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], promoted properties enable various BizTalk Server components to access key items of data, known in this context as distinguished fields and property fields that arrive within an instance message without needing to know how to look for them within the message itself. For different types of messages, you can determine which items of data require promotion to a more visible level. Depending on how you choose to promote such fields, you may need to create and define an associated property schema.  
  
> [!NOTE]
>  Promoted properties are restricted to non-repeating elements/attributes.  
  
 Distinguished fields are accessible only within orchestrations and do not require the creation of a corresponding property schema. If you only need to access promoted message data from within an orchestration, you can promote the data as one or more distinguished fields.  
  
 Property fields are accessible from within various BizTalk Server components, including pipelines and orchestrations. Property fields can also be used for message routing. If you need to access promoted message data from contexts other than within orchestrations, you must create one or more property schemas to describe the data you are promoting.  
  
 A property schema is a special schema that you associate with a message schema. It is used for promoting specific values from within an instance message into the message context. Property promotion provides a centralized mechanism for pulling key pieces of information that you define from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server.  
  
## Create property schema overview
 You can automatically create a default property schema by using the quick promotion feature of BizTalk Server. This is the easiest way to create the property schema required for property field promotion. For more information about how to perform quick promotions, see [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).  
  
 You can also create new property schema. When a BizTalk project is open, select the BizTalk project, right-click and select **Add**, click **New Item**, and then click **Schema**.  
  
> [!NOTE]
>  - If a property schema is associated with a message schema, then these two must be in the same BizTalk project. Separating property schema from its associated message schema in different BizTalk projects is not supported.  
>
>  - If you have two property schemas that have the same namespace, even though they are defined in different assemblies, the schemas will not resolve properly at runtime. You will get a routing failure at runtime.  

## Distinguished fields and property fields 
 There are two types of property promotion: distinguished fields and property fields. The latter type uses property schemas. In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which you access by using the **Promote Properties** property of the **Schema** node.  
  
> [!NOTE]
>  - There are some restrictions on values that you can promote. For more information, see the table in [Promoting Properties](../core/promoting-properties.md).  
>
>  - Distinguished fields do not appear in filter expressions. Only property fields appear in filter expressions.  
  
 Property schemas are simple when compared to message schemas. In the schema tree, you are only allowed to insert **Field Element** nodes as immediate child nodes of the **Schema** node, creating a structure that is two levels deep. For the most part, you set the properties of the **Field Element** nodes as you would for **Field Element** nodes appearing in a message schema. You are limited to using only XSD simple types.  
  
> [!IMPORTANT]
>  You should not rename any schema that is being used by another schema. This includes property schemas for which promotions have already been established. If you do so, the schema that is being used will not be able to find the other schema because the name it contains will no longer be accurate.  
  
 The **Property Schema Base** property is unique to **Field Element** nodes as they appear in property schemas. This property is blank by default, but can be set to either **MessageDataPropertyBase** or **MessageContextPropertyBase**, resulting in a **propSchFieldBase** attribute being added to the **fieldInfo** annotation element with one or the other of these values.  
  
 When the **propSchFieldBase** attribute is set to **MessageDataPropertyBase**, it means that the value of the promoted property corresponds to data in the message, such as the value of some field. When the **propSchFieldBase** attribute is set to **MessageContextPropertyBase**, it means that the value of the promoted property may be from somewhere else, such as an envelope, or that it may be set by a pipeline component.  
  
 **Field Element** nodes in property schemas also have a property called **Sensitive Information**, which when set to **Yes**, will keep the corresponding value from being visible from within BizTalk Explorer and message event and service instance tracking, thereby preserving its sensitive nature.  See **Sensitive Information** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for more details.
  
 The following XML Schema definition (XSD) language representation of a property schema contains an annotation associated with the schema element that identifies this schema as a property schema (schema_type="property"). It also contains three **Field Element** nodes below the **Schema** node. The first **Field Element** node, named PromProp1, does not have a value defined for its **Property Schema Base** property, but the latter two **Field Element** nodes have that property set to **MessageDataPropertyBase** and **MessageContextPropertyBase**, respectively.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
           targetNamespace="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
       <xs:appinfo>  
  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>  
  
```  
  
## See Also  
 [Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md)