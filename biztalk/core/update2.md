---
description: "Learn how to use the Update element to extract data from an event and import it into the related Business Activity Monitoring (BAM) activity."
title: "Update2"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Update

The `Update` element is used to extract data from an event and import it into the related BAM activity.  
  
## Format
  
To use the `Update` element, you must provide both a column name and type and an **Expression** element containing one or more **Operation** elements that evaluate to a single string value.  
  
```  
<ic:Update DataItemName="Name" Type="Type">  
  <ic:Expression>  
    <!-- one or more Operation elements -->  
  </ic:Expression>  
</ic:Update>  
```  
  
### Attributes  
  
|Attribute name|Description|  
|--------------------|-----------------|  
|ColumnName|BAM activity checkpoint name. This is the checkpoint that will be updated with the extracted data.|  
|Type|BAM data type of the checkpoint; must be one of the following:<br /><br /> -   NVARCHAR<br />-   DATETIME<br />-   INT<br />-   FLOAT|  
  
## Remarks  
 The following operations are not supported in the `Update` expression:  
  
- And  
  
- Equals  
  
## Example
  
In the following example, the **GetContextProperty** WF operation is used to retrieve the **EventTime** property. This value will be stored as a **DATETIME** type for the "StartOrderProcessing" data item for the BAM activity.  
  
```  
<ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
## See Also
  
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)
