---
title: Date and Time Functoid
TOCTitle: Date and Time Functoid
ms:assetid: dc2597f1-3031-4934-b42e-eac70df80994
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561424(v=BTS.80)
ms:contentKeyID: 51532767
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Date and Time Functoid

 

Use the **Date and Time** functoid ( ![](images/Aa577839.0034ab3d-3317-4927-82fe-7d1d90d3044b(BTS.80).jpeg)) to retrieve the current date and time in the format YYYY-MM-DDThh:mm:ss.

## Input

None.

## Output

**Output 1:** A date/time string in the format YYYY-MM-DDThh:mm:ss that represents the current date and time.

## Remarks

The date and time formats used by this functoid are ISO 8601-compliant.

This functoid can be useful when a field in a destination message that is being created from a source message and a map is meant to contain a time stamp, such as the date and time when the message was processed.

The time portion of the output of this functoid is expressed by using a 24 hour notation (for example, 2 P.M. is expressed as "14:00:00").

## See Also

[Date and Time Functoids Reference](date-and-time-functoids-reference.md)  
[Date and Time Functoids](https://msdn.microsoft.com/library/aa559411\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

