---
description: "Learn more about: Error - XML Input File Does Not Exist"
title: "Error - XML Input File Does Not Exist"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.xmlInputFileDoesNotExist"
---
# Error - XML Input File Does Not Exist
**Error Code**  
  
 btm1039  
  
 **Explanation**  
  
 The XML input instance message file specified for the Test Map operation does not exist. When the value of the **TestMap Input** map property is set to XML, you must specify an existing XML instance message file for the **TestMap Input Instance** map property.  
  
 **User Action**  
  
 Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property. Using the **Select Input File** dialog box, select an existing XML instance message file that conforms to the source schema of the map. Alternatively, you can type the path of this XML file directly into the value field of the **TestMap Input Instance** property.
