---
description: "Learn more about: Error - Native Input File Does Not Exist"
title: "Error - Native Input File Does Not Exist"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.nativeInputFileDoesNotExist"
---
# Error - Native Input File Does Not Exist
**Error Code**  
  
 btm1040  
  
 **Explanation**  
  
 The native input instance message file specified for the Test Map operation does not exist. When the value of the **TestMap Input** map property is set to **Native**, you must specify an existing native instance message file for the **TestMap Input Instance** map property.  
  
 **User Action**  
  
 Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property. In the **Select Input File** dialog box, select an existing native instance message file that conforms to the source schema of the map. Alternatively, you can type the path of this native file directly into the value field of the **TestMap Input Instance** property.
