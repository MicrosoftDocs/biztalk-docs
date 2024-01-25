---
description: "Learn more about: Data Transformation"
title: "Data Transformation"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Transformation
Mapping data relies on data transformation.  
  
 Data transformation is the process of creating a correspondence between records and fields of a source schema to (often different) records and fields in a destination schema. An example of data transformation is to map shipping and billing address information from a purchase order to an invoice. This is the most basic type of mapping. Data transformation can also apply to operations such as:  
  
- Averaging data from a looping record and sending the output to a single field in the destination schema.  
  
- Converting character data to its ASCII format.  
  
- Adding or subtracting data from one or more records and putting the result in a single field in the destination schema.  
  
  If you want to translate data from one format to another, you would use a pipeline. This can be helpful in solving enterprise application integration problems by translating a given type of message into alternative formats required by existing systems but cannot be done using a map.  
  
## See Also  
 [Maps](../core/maps.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)
