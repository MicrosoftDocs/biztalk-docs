---
description: "Learn more about: Value Extractor Functoid"
title: Value Extractor Functoid
TOCTitle: Value Extractor Functoid
ms:assetid: 45a9a968-b100-4812-884a-f18879afc9c7
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559864(v=BTS.80)
ms:contentKeyID: 51527666
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Value Extractor Functoid

 

Use the **Value Extractor** functoid ( ![Icon that represents the Value Extractor functoid.](images/Aa562112.8a16abc4-981d-49cb-87e5-6bb7b57b8cf0(BTS.80).jpeg)) to extract the value from a specified column in a Microsoft ActiveX Data Objects (ADO) recordset, which is returned by the **Database Lookup** functoid.

## Input

**Parameter 1:** An ADO recordset, which is the output of the **Database Lookup** functoid. This recordset never contains more than one database row.

**Parameter 2:** The name of a column from which to extract a value for output.

## Output

**Output 1:** A value from the specified column in the single-row ADO recordset that was retrieved by using the **Database Lookup** functoid.

## Remarks

To avoid errors that are only detected at run time, make sure that the first parameter to the **Value Extractor** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the **Database**category or custom functoid that returns an ADO recordset.

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))  
[Database Lookup Functoid](database-lookup-functoid.md)  
[Error Return Functoid](error-return-functoid.md)

