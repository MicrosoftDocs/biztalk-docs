---
title: "Basic and Complex Mapping Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da864b48-6255-4847-9a6f-13e489e8658d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic and Complex Mapping Operations
BizTalk Mapper provides solutions for a variety of mapping scenarios ranging from simple parent-child tree-type operations to detailed, complex operations involving looping records and hierarchies. The complexity of a mapping scenario depends on your preferences and business needs—XML Schema definition (XSD) language gives you considerable flexibility in defining structured formats. Almost all mapping scenarios fall into one of two categories: basic mapping and complex mapping.  
  
## Basic Mapping  
 Basic mapping is the most common type of mapping you can create. In a basic map, input and output items have a one-to-one relationship. An input item maps to one and only one output item. Although many types of transformations and translations are possible with basic mapping, such as using multiple *functoids* and cascading functoids to manipulate the value being copied, the underlying scenario remains relatively simple. Basic mapping operations also include mapping fields from two different parent records (occurring only once) to fields under a single parent record in the destination schema.  
  
## Complex Mapping  
 Complex mapping involves records or fields that occur multiple times for a single instance of the **Record** or **Field Element** node in the schema tree. Such nodes have their **Max Occurs** property set to a value greater than one (1), indicating there may be more than one corresponding element in an instance message. When a BizTalk map uses this type of variable count mapping (also known as *looping*), the Extensible Stylesheet Language (XSL) style sheet compiler must be able to determine the proper loop path over which to iterate to produce the required output.  
  
 In general, you can link a field in a looping record in the source schema to a field in a looping record in the destination schema. The number of corresponding elements in an input instance message determines the number of elements created in the output instance message. Consider the following XSD fragments from example source and destination schemas.  
  
### Source Schema Fragment  
  
```  
<xs:element minOccurs="1" maxOccurs="5"  
            name="SrcLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
```  
  
### Destination Schema Fragment  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded"  
            name="DstLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
```  
  
 In these fragments:  
  
- **SrcLoopingRecord**, a **Record** node in input instance messages, can occur from one to five times. It also contains the child **Field Element** nodes **Field1** (a string) and **Field2** (an integer) that occur once for each instance of their parent.  
  
- **DstLoopingRecord**, a **Record** node in output instance messages, can occur zero (0) or more times, unbounded. It also contains the child **Field Element** nodes **FieldA** (a string) and **FieldB** (an integer) that occur once for each instance of their parent.  
  
  Assuming that Field1 is mapped to FieldA and Field2 is mapped to FieldB, and that the following fragment from an input instance message has processed those mappings, the following fragment from an output instance message would be produced.  
  
### Input Instance Message Fragment  
  
```  
<SrcLoopingRecord>  
    <Field1>A string</Field1>  
    <Field2>10</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>Another string</Field1>  
    <Field2>11</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>A ball of string</Field1>  
    <Field2>12</Field2>  
</SrcLoopingRecord>  
```  
  
### Output Instance Message Fragment  
  
```  
<DstLoopingRecord>  
    <FieldA>A string</FieldA>  
    <FieldB>10</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
  <FieldA>Another string</FieldA>  
  <FieldB>11</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
    <FieldA>A ball of string</FieldA>  
    <FieldB>12</FieldB>  
</DstLoopingRecord>  
```  
  
 The number of occurrences of the **SrcLoopingRecord** element in the input instance message (3) determines the number of occurrences of the **DstLoopingRecord** element in the output instance message.  
  
 A type of mapping not supported by BizTalk Mapper is the use of multiple loop paths. This type of mapping involves fields from two or more looping records in the source schema being mapped to fields within a single looping record in the destination schema. This presents a problem—there is no effective way to determine the number of elements to produce in the output instance message. Multiple loop paths result in a map compilation warning indicating that the destination node has multiple source loop paths. However, this is only a warning, and the number of iterations in the first source loop path is used to determine the number of elements produced in the output instance message. You can take explicit control of looping behavior by using the **Looping** functoid.  
  
 Microsoft BizTalk Server introduced a new kind of looping called table-driven looping. Table-driven looping is useful when your output instance message needs to be based on data from the input instance message, combined with one or more constants, links from the source schema, or functoids. In such cases, the output instance message can have multiple records based on data from a single record in the input instance message that is combined with different constants, or based on data coming from multiple records in the input instance message. For more information about table-driven looping using the **Table Looping** and **Table Extractor** functoids, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)