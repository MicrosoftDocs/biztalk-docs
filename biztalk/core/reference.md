---
description: "Learn more about: Reference"
title: "Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b916c55a-c84c-4008-8927-f8e584c36fe9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Reference
The **Reference** element can be used to add one or more relationships to a BAM activity. This is useful when you want to attach a pointer like a primary key, ID, or URL to a related message. For example, you might store a reference to a Shipment Batch in a Purchase Order activity.

## Format
 The `Reference` element supports both the **Data** and **LongData** child elements that contain an expression specifying the data to attach to the BAM activity. You can use any combination of **Data** and **LongData** to meet your tracking requirements.

### Attributes

|Attribute name|Description|
|--------------------|-----------------|
|Name|Name of the relationship that will be attached to the BAM activity.|
|Type|Arbitrary string specifying the type of relationship that will be attached to the BAM activity. Both arbitrary strings and the following predefined BAM types are supported:<br /><br /> -   BizTalkService<br />-   MessageID<br />-   Activity<br />-   DocumentUrl<br />-   InstanceID<br /><br /> For more information on predefined BAM reference types, see [Reference Properties](/previous-versions/).|

### Child Elements

|Execution status|Description|
|----------------------|-----------------|
|Data|Specifies how to extract string data up to 128 characters that will be attached to the BAM activity.|
|LongData|Specifies how to extract arbitrarily long string data that will be attached to the BAM activity.|

> [!NOTE]
>  A `Reference` element can combine one or more **Data** and **LongData** child elements as needed.

## Remarks
 The following common operations are not allowed in Reference expressions:

-   And

-   Equals

## Example
 In the following sample, a reference named "Related Document" of type "DocumentUrl" is created using `GetUserData` for a workflow. Because the user data is expected to be fewer than 1024 characters in length, the `Data` element is used to contain the `Expression` element.

```
<ic:Reference Name="Related Document" Type="DocumentUrl">
  <ic:Data>
    <ic:Expression>
      <wf:Operation Name="GetUserData" />
    </ic:Expression>
  </ic:Data>
</ic:Reference>
```

 The **Reference** element supports a mix of `Data` and `LongData` elements. In the following sample, the country name and note fields from a purchase order are retrieved from a WCF service and written to the relationship "Long and Short Data" as type "MyType". Because the note field supports more than 1024 characters, the expression is enclosed in a `LongData` element.

```
<ic:Reference Name="Long and Short Data" Type="MyType">
  <ic:Data>
    <ic:Expression>
      <ic:Operation Name="Constant">
        <ic:Argument>Country: </ic:Argument>
      </ic:Operation>
      <wcf:Operation Name="XPath">
        <wcf:Argument>//s:Body//po:Country</wcf:Argument>
      </wcf:Operation>
       <ic:Operation Name="Concatenate" />
    </ic:Expression>
  </ic:Data>
  <ic:LongData>
    <ic:Expression>
      <ic:Operation Name="Constant">
        <ic:Argument>Note: </ic:Argument>
      </ic:Operation>
      <wcf:Operation Name="XPath">
        <wcf:Argument>//s:Body//po:Note</wcf:Argument>
      </wcf:Operation>
      <ic:Operation Name="Concatenate" />
    </ic:Expression>
  </ic:LongData>
</ic:Reference>
```

## See Also
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)
 [EventStream.AddRelatedActivity Method](/previous-versions/)