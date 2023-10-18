---
description: "Learn more about: Error - Input File Does Not Exist"
title: "Error - Input File Does Not Exist"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.inputFileDoesNotExist"
---
# Error - Input File Does Not Exist
**Error Code**  
  
 btm1037  
  
 **Explanation**  
  
 The input instance message file specified for the Test Map operation does not exist, and the type of the Test Map input is not set to **Generate Instance**. When the value of the **TestMap Input** map property is not set to **Generate Instance**, you must specify an existing instance message file for the **TestMap Input Instance** map property.  
  
 **User Action**  
  
 As appropriate, set one or the other of the following map properties:  
  
-   **TestMap Input Instance.** Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property. Using the **Select Input File** dialog box, select an existing instance message file that conforms to the source schema of the map. Alternatively, you can type the path of this file directly into the value field of the **TestMap Input Instance** property.  
  
-   **TestMap Input.** To avoid specifying an input instance message file, right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab of the **Property Pages** dialog box for the map, use the drop-down list in the value field of the **TestMap Input** property to select **Generate Instance**. In this case, you need not specify a file for the **TestMap Input Instance** property.
