---
description: "Learn more about: EDI Data Element Structural Element"
title: "EDI Data Element Structural Element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EDI Data Element Structural Element
The data element is the primary unit of data in the message. Data elements are separated by the data element separator, which is an asterisk by default for X12 and a plus sign by default for EDIFACT. The optionality of data elements is defined as mandatory, optional, or conditional.  
  
 A data element can be either simple or composite. Simple data elements are numeric and are the lowest level of data. Composite data elements are concatenations of sub element, which are simple data elements separated by a component separator. By default, the component separator is the colon for X12 and EDIFACT.  
  
 For EDIFACT-encoded messages, if the data to be sent via EDI needs to send any character defined for use as a separator, you need to use a release character to indicate that the following character is not a separator, but is part of the data. The release character is by default the question mark (?).  
  
> [!NOTE]
>  A release character is not supported for X12. If a separator is encountered as part of the data of an X12-encoded interchange, on either the receive or send side, the interchange will be suspended.
