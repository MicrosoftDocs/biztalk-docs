---
title: Scientific Functoids Reference
TOCTitle: Scientific Functoids Reference
ms:assetid: e60738d7-9df9-4c73-91cc-692a6d481d4f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561631(v=BTS.80)
ms:contentKeyID: 51533012
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Scientific Functoids Reference

 

Use **Scientific** functoids to perform a variety of standard trigonometric, logarithmic, and exponential calculations.


> [!IMPORTANT]
> <P>Because Microsoft BizTalk Server uses the underlying functionality of the .NET Framework, the results produced by some of the <STRONG>Scientific</STRONG> functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. For example, very large values returned as output of these functoids may be returned as "Infinity" rather than an exponential value. You should test your maps thoroughly to ensure that you are getting the results you expect.</P>



When a **Scientific** functoid determines that one or more of its input parameters is not valid, it cancels the operation and returns an empty string, such that a field in an output instance message is created as "\<FieldName\>\</FieldName\>" and the string [Size](size-functoid.md) functoid returns zero (0).

When the input parameter descriptions specify a numeric value, strings that can be interpreted as numbers are also accepted.

For conceptual information about **Scientific** functoids, see [Scientific Functoids](https://msdn.microsoft.com/library/aa546775\(v=bts.80\)).

The following table shows the functoids in the **Scientific** category.

<table>
<thead>
<tr class="header">
<th>Scientific functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa547865.34aadbe8-9246-43d9-a8f9-a412570c60af(BTS.80).jpeg" /> <a href="10-n-functoid.md">10^n</a></td>
<td>Returns the number 10 raised to a specified power.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560104.736b531e-2637-4003-a6d7-969685908433(BTS.80).jpeg" /> <a href="arc-tangent-functoid.md">Arc Tangent Functoid</a></td>
<td>Returns the arc tangent of a number.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa577698.d6097cf2-19c9-47e6-bf1a-a111e1f43d6d(BTS.80).jpeg" /> <a href="base-specified-logarithm-functoid.md">Base-Specified Logarithm</a></td>
<td>Returns the base-specified logarithm of a value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561818.f7605010-54a7-476d-865e-711454b32e47(BTS.80).jpeg" /> <a href="common-logarithm-functoid.md">Common Logarithm</a></td>
<td>Returns the base 10 logarithm of a value.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559678.3ec59432-420e-42e9-816f-45ef26487f54(BTS.80).jpeg" /> <a href="cosine-functoid.md">Cosine</a></td>
<td>Returns the cosine of an angle.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559669.10eb4753-35d8-4cce-a311-909a98157f9e(BTS.80).jpeg" /> <a href="natural-exponential-functoid.md">Natural Exponential Function</a></td>
<td>Returns <strong>e</strong> raised to a specified power.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa561631.77f2b922-d1ce-44ab-8c30-4d899698f93e(BTS.80).jpeg" /> <a href="natural-logarithm-functoid.md">Natural Logarithm</a></td>
<td>Returns the base <strong>e</strong> logarithm of a value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561631.858e7775-ff7e-4c62-9f1c-a24c7d7cb488(BTS.80).jpeg" /> <a href="sine-functoid.md">Sine</a></td>
<td>Returns the sine of an angle.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559950.3923b2f3-4edd-4d67-b7db-bac28447c7ad(BTS.80).jpeg" /> <a href="tangent-functoid.md">Tangent</a></td>
<td>Returns the tangent of an angle.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561631.d9f9d238-b44d-498f-bf7f-cbd8b56bef77(BTS.80).jpeg" /> <a href="x-y-functoid.md">X^Y</a></td>
<td>Raises a specified value to the power of another specified value.</td>
</tr>
</tbody>
</table>


## See Also

[Scientific Functoids](https://msdn.microsoft.com/library/aa546775\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

