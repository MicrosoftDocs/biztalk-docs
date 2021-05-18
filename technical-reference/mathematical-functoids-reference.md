---
description: "Learn more about: Mathematical Functoids Reference"
title: Mathematical Functoids Reference
TOCTitle: Mathematical Functoids Reference
ms:assetid: 4346ed03-172f-4182-9219-8e2e06f88867
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559820(v=BTS.80)
ms:contentKeyID: 51527596
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Mathematical Functoids Reference

 

Use **Mathematical** functoids to perform a variety of basic mathematical operations.


> [!IMPORTANT]
> <P>Because Microsoft BizTalk Server uses the underlying functionality of the .NET Framework, the results produced by some of the <STRONG>Mathematical</STRONG> functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. You should test your maps thoroughly to ensure that you are getting the results you expect.</P>



When a **Mathematical** functoid determines that one or more of its input parameters is not valid, it cancels the operation and returns an empty string, such that a field in an output instance message is created as "\<FieldName\>\</FieldName\>" and the string [Size](size-functoid.md) functoid returns zero (0).

When the input parameter descriptions specify a numeric value, strings that can be interpreted as numbers are also accepted.

For conceptual information about **Mathematical** functoids, see [Mathematical Functoids](https://msdn.microsoft.com/library/aa559213\(v=bts.80\)).

The following table shows the functoids in the **Mathematical** category.

<table>
<thead>
<tr class="header">
<th>Mathematical functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa561898.f16947e6-6c6e-4a38-bc1f-446d8e0d2e17(BTS.80).jpeg" alt="Icon that represents the Absolute Value functoid."/> <a href="absolute-value-functoid.md">Absolute Value</a></td>
<td>Calculates the absolute value of the specified value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560388.f6095b67-496f-4c2d-bf90-0480f18d4b5a(BTS.80).jpeg" alt="Icon that represents the Addition functoid."/> <a href="addition-functoid.md">Addition</a></td>
<td>Calculates the sum of the numeric input parameters.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa578425.9a73420a-40d6-4dc4-8b06-4cb1c2b2afd4(BTS.80).jpeg" alt="Icon that represents the Division functoid."/> <a href="division-functoid.md">Division</a></td>
<td>Calculates the quotient of the specified dividend and divisor.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560329.93d37f07-a527-4d12-8872-d7856e652c34(BTS.80).jpeg" alt="Icon that represents the Integer functoid."/> <a href="integer-functoid.md">Integer</a></td>
<td>Returns the integer portion of a numeric input parameter.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559820.ae1a9133-f2fe-4b48-b33f-ee2ed97737de(BTS.80).jpeg" alt="Icon that represents the Maximum Value functoid."/> <a href="maximum-value-functoid.md">Maximum Value</a></td>
<td>Determines the largest value among the numeric input parameters.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561708.6635d089-292f-447f-b612-984e0b969c46(BTS.80).jpeg" alt="Icon that represents the Minimum Value functoid."/> <a href="minimum-value-functoid.md">Minimum Value</a></td>
<td>Determines the smallest value among the numeric input parameters.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa578260.03bb8442-536b-466d-b7ee-dac5a21f28f5(BTS.80).jpeg" alt="Icon that represents the Modulo functoid."/> <a href="modulo-functoid.md">Modulo</a></td>
<td>Calculates the remainder of the specified integer division.</td>
</tr>
<tr class="even">
<td><img src="images/Aa547077.9a5b9d47-f92f-4aa9-a893-4fe748de4ea5(BTS.80).jpeg" alt="Icon that represents the Multiplication functoid."/> <a href="multiplication-functoid.md">Multiplication</a></td>
<td>Calculates the product of the numeric input parameters.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa577673.ff25c636-ba90-404f-a911-eee519eade0c(BTS.80).jpeg" alt="Icon that represents the Round functoid."/> <a href="round-functoid.md">Round</a></td>
<td>Rounds the specified numeric input parameter to the nearest specified number of decimal places.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559035.ee5224d4-3eaa-45d7-81ae-9909f2a21126(BTS.80).jpeg" alt="Icon that represents the Square Root functoid."/> <a href="square-root-functoid.md">Square Root</a></td>
<td>Calculates the square root of a specified numeric value.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa558800.3ff3db5e-b89d-46fa-aadb-3966ac9eea56(BTS.80).jpeg" alt="Icon that represents the Subtraction functoid."/> <a href="subtraction-functoid.md">Subtraction</a></td>
<td>Calculates the result of subtracting up to 99 numeric values from another numeric value.</td>
</tr>
</tbody>
</table>


## See Also

[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

