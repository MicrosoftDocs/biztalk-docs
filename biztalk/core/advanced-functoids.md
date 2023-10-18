---
description: "Learn more about: Advanced Functoids"
title: "Advanced Functoids"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Advanced Functoids

## Overview
Advanced functoids fall into five groups, according to their use:  
  
-   **Managing looping records.** The **Index**, **Iteration**, **Looping**, **Nil Value**, **Record Count**, **Table Extractor**, and **Table Looping** functoids are used in various combinations when the input instance message contains sections with an unpredictable number of repeating elements, as represented by looping records in the source schema.  
  
-   **Conditional mapping.** The **Value Mapping** and **Value Mapping (Flattening)** functoids are used to provide conditional mapping from an input instance message to an output instance message. When their first input parameter is true, the second input parameter is put into the specified element or attribute in the output instance message; otherwise, that element or attribute is not created in the output instance message.  
  
-   **Arbitrary scripting.** The **Scripting** functoid is used to run arbitrary script or compiled code when an input instance message is being mapped to an output instance message. Such script or compiled code can be created so that it accepts input parameters from the source instance message, from configured constant values, from the output of another functoid, or some combination thereof.  
  
-   **Simple mapping.** The **Mass Copy** functoid can be used to copy an entire element, including its subelements to an arbitrary depth, from an input instance message to an output instance message.  
  
-   **Troubleshooting**. The **Assert** functoid can be used to test your assumptions about element values.  
  
## Available functoids
  
 The **Advanced** functoids are: 

* Assert Functoid
* Index Functoid 
* Iteration Functoid 
* Looping Functoid 
* Mass Copy Functoid 
* Nil Value Functoid
* Record Count Functoid 
* Scripting Functoid 
* Table Looping and Table Extractor Functoids
* Value Mapping Functoid
* Value Mapping (Flattening) Functoid

More details on these functoids are in the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps
  
-   [Assert Functoid](../core/assert-functoid.md)  
  
-   [Index Functoid](../core/index-functoid.md)  
  
-   [Iteration Functoid](../core/iteration-functoid.md)  
  
-   [Looping Functoid](../core/looping-functoid.md)  
  
-   [Mass Copy Functoid](../core/mass-copy-functoid.md)  
  
-   [Nil Value Functoid](../core/nil-value-functoid.md)  
  
-   [Record Count Functoid](../core/record-count-functoid.md)  
  
-   [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md)  
  
-   [Value Mapping Functoid](../core/value-mapping-functoid.md)  
  
-   [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md)  
  
-   [Scripting Functoid](../core/scripting-functoid.md)
