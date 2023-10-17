---
description: "Learn more about: Warning - Field Data Type Mismatch"
title: "Warning - Field Data Type Mismatch"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.fieldDataTypeMismatch"
---
# Warning - Field Data Type Mismatch
**Error Code**  
  
 BEC1002  
  
 **Explanation**  
  
 The **Data Type** property of the indicated node was found to be different than the **Data Type** property of the **Field Element** node to which it is being promoted in the corresponding property schema. The data type of a node in a schema should match the data type assigned to the **Field Element** node used for its Property Field promotion, or at least, the assigned data types should map to the same common language runtime (CLR) type.  
  
 **User Action**  
  
 Change the **Data Type** properties of the indicated node and the **Field Element** node to which it is being promoted to the same data type value, or at least to data type values that map to the same CLR data type.
