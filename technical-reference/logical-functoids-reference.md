---
description: "Learn more about: Logical Functoids Reference"
title: Logical Functoids Reference
TOCTitle: Logical Functoids Reference
ms:assetid: e64b6106-4ac1-460e-b214-f655820428bd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561635(v=BTS.80)
ms:contentKeyID: 51533020
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Logical Functoids Reference

 

Use **Logical** functoids to perform a variety of logical operations, often controlling whether a particular element or attribute is created in an output instance message.


> [!IMPORTANT]
> <P>Because Microsoft BizTalk Server uses the underlying functionality of the .NET Framework, the results produced by some of the <STRONG>Logical</STRONG> functoids may vary from the equivalent functoids in earlier versions of BizTalk Server. For example, <STRONG>Logical</STRONG> functoids are case-sensitive when comparing two strings: "Abc" and "abc" are not equal. The exception to this rule is when <STRONG>Logical</STRONG> functoids compare strings that represent the Boolean values <STRONG>True</STRONG> and <STRONG>False</STRONG>:"True" and "true" are equal. You should test your maps thoroughly to ensure that you are getting the results you expect.</P>



Unless otherwise noted, **Logical** functoids always output a Boolean value, either **True** or **False**. This means that you cannot use the output of a **Logical** functoid as the input to a functoid that is expecting a string, such as the **Uppercase** functoid, hoping to yield an output string like "TRUE". In other words, you should not connect the output of a logical functoid to a node and expect that field to be populated with a string value of "TRUE" or "FALSE" or variant ("True", "true", "False", "false", etc).

On the other hand, **Logical** functoids do accept a few different data types (Boolean values, strings, and numbers) as input values. They use standard semantics to interpret and compare such values. The best practice is to pass two parameters of the same data type, which results in the following actions:

  - When both input parameters are Boolean values, a logical comparison is performed.

  - When both input parameters are numbers, both are converted to Boolean values where non-zero values become Boolean **True** and zero values become Boolean **False**, followed by a logical comparison.

  - When both input parameters are strings, a case-sensitive string comparison is performed. If appropriate, use either the [Uppercase](uppercase-functoid.md) or [Lowercase](lowercase-functoid.md) functoid to force both input strings to the same case. Note that passing strings to the **Logical AND**, **Logical NOT**, and **Logical OR** functoids does not yield meaningful results.

The following two obscure cases are also supported:

  - If one input parameter is a number and the other input parameter is a string, a case-sensitive string comparison is performed. This means that the string needs to be a string version of a number for the comparison to be meaningful.

  - If one input parameter is Boolean and the other input parameter is a string, use the literal string "true" (case-sensitive) to represent the Boolean value **True** and the literal string "false" (case-sensitive) to represent the Boolean value **False**. Other string values for **True** and **False** are not supported for all **Logical** functoids, including differences in case only.

Passing a Boolean input parameter and a numeric input parameter is not supported in a meaningful way.

For conceptual information about **Logical** functoids, see [Logical Functoids](https://msdn.microsoft.com/library/aa561580\(v=bts.80\)).


> [!IMPORTANT]
> <P>When the output of any logical functoid is directly linked to a target schema node, on doing a test map, you do not get a logical value (true/false) as the output. It is rendered as blank. Therefore, the output of a logical value should be connected only to those functoids which accept logical input parameters.</P>



The following table shows the functoids in the **Logical** category.

<table>
<thead>
<tr class="header">
<th>Logical functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa559045.63f9f006-01a4-405d-a197-e9e945144158(BTS.80).jpeg" alt="Icon that represents the Equal functoid."/> <a href="equal-functoid.md">Equal</a></td>
<td>Tests whether the two input parameters are equal.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561635.6d9c0016-6926-4409-916b-d753b419ad06(BTS.80).jpeg" alt="Icon that represents the Greater Than functoid."/> <a href="greater-than-functoid.md">Greater Than</a></td>
<td>Tests whether the first input parameter is greater than the second input parameter.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562017.841a6c54-e118-4ece-ad14-9901823ed172(BTS.80).jpeg" alt="Icon that represents the Greater Than or Equal To functoid."/> <a href="greater-than-or-equal-to-functoid.md">Greater Than or Equal To</a></td>
<td>Tests whether the first input parameter is greater than or equal to the second input parameter.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561802.427a7da4-80ee-4005-9c42-10b25e143ed6(BTS.80).jpeg" title="Logical IsNil functoid" alt="Logical IsNil functoid"/> <a href="isnil-functoid.md">IsNil</a></td>
<td>Test whether the input parameter is Nil.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa578105.691e9794-9b7c-4981-acdd-2c309afbdb2d(BTS.80).jpeg" alt="Icon that represents the Less Than functoid."/> <a href="less-than-functoid.md">Less Than</a></td>
<td>Tests whether the first input parameter is less than the second input parameter.</td>
</tr>
<tr class="even">
<td><img src="images/Aa547601.75d94c98-468e-41dd-8a31-b9c566a0bd84(BTS.80).jpeg" alt="Icon that represents the Less Than or Equal To functoid."/> <a href="less-than-or-equal-to-functoid.md">Less Than or Equal To</a></td>
<td>Tests whether the first input parameter is less than or equal to the second input parameter.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560432.41ec41a2-63f0-407e-b3ee-9fa613cfd516(BTS.80).jpeg" alt="Icon that represents the Logical AND functoid."/> <a href="logical-and-functoid.md">Logical AND</a></td>
<td>Determines whether all of the specified input parameters are true.</td>
</tr>
<tr class="even">
<td><img src="images/Aa577573.d77fb1a1-4472-4830-8e02-43cf3b396d9e(BTS.80).jpeg" alt="Icon that represents the Logical Date functoid."/> <a href="logical-date-functoid.md">Logical Date</a></td>
<td>Determines whether the input parameter is a date.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559386.484702af-934c-4017-9b5a-c2d9fc94be51(BTS.80).jpeg" alt="Icon that represents the Logical Existance functoid."/> <a href="logical-existence-functoid.md">Logical Existence</a></td>
<td>Determines whether the record or field that is linked to it exists in a particular source instance message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561635.b4090252-3b23-45c4-ae46-1599420440a4(BTS.80).jpeg" title="Logical NOT functoid" alt="Logical NOT functoid"/> <a href="logical-not-functoid.md">Logical NOT</a></td>
<td>Returns the logical inverse of the input parameter.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa577628.d53b1a3c-b6cc-49a7-b62b-3be74432ea44(BTS.80).jpeg" alt="Icon that represents the Logical Numeric functoid."/> <a href="logical-numeric-functoid.md">Logical Numeric</a></td>
<td>Determines whether the input parameter is a numeric value.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560272.82f62b4d-fa44-4ce1-98cb-75030ae40a59(BTS.80).jpeg" alt="Icon that represents the Logical OR functoid."/> <a href="logical-or-functoid.md">Logical OR</a></td>
<td>Determines whether any of the specified input parameters are true.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa560607.62d28c15-1e58-4bf5-9568-c636d468d77d(BTS.80).jpeg" alt="Icon that represents the Logical String functoid."/> <a href="logical-string-functoid.md">Logical String</a></td>
<td>Determines whether the input parameter is a string.</td>
</tr>
<tr class="even">
<td><img src="images/Aa560651.6faf9c11-7753-4b84-aaa4-60ad731bf6f4(BTS.80).jpeg" alt="Icon that represents the Not Equal functoid."/> <a href="not-equal-functoid.md">Not Equal</a></td>
<td>Tests whether the two input parameters are not equal.</td>
</tr>
</tbody>
</table>


## See Also

[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

