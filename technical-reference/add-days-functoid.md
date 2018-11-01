---
title: Add Days Functoid
TOCTitle: Add Days Functoid
ms:assetid: e59aaf65-864f-49ac-a8d4-b67ac4c00d3d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561626(v=BTS.80)
ms:contentKeyID: 51533028
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Add Days Functoid

 

Use the **Add Days** functoid ( ![](images/Aa561626.03aafb6a-0b02-4076-a1c4-4ab438f08007(BTS.80).jpeg)) to add a specified number of days to a specified date.

## Input

**Parameter 1:** A date string in the format YYYY-MM-DD or a date/time string in the format YYYY-MM-DDThh:mm:ss to which the specified number of days is added.

**Parameter 2:** A numeric value that is interpreted as the number of days to be added to the specified date.

## Output

**Output 1:** A date string in the format YYYY-MM-DD that is the result of adding the specified number of days to the specified date.

## Remarks

The date format used by this functoid is ISO 8601-compliant.

For example, suppose that your company always fulfills purchase orders within two days of receiving them. When you create a map that creates a purchase order acknowledgment from a purchase order, you can use the **Add Days** functoid to add two days to the current date (returned by the **Date** functoid) and use that value in the acknowledgment as the date by which the purchase order will be fulfilled.

## See Also

[Date and Time Functoids Reference](date-and-time-functoids-reference.md)  
[Date and Time Functoids](https://msdn.microsoft.com/en-us/library/aa559411\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/en-us/library/aa560635\(v=bts.80\))

