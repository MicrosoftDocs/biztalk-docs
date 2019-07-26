---
title: Conversion Functoids Reference
TOCTitle: Conversion Functoids Reference
ms:assetid: b77f6dd9-9a0e-460c-8b17-a1d3bec7212d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578277(v=BTS.80)
ms:contentKeyID: 51530724
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Conversion Functoids Reference

 

Use **Conversion** functoids to perform a variety of standard character and numeric base conversion calculations.


> [!IMPORTANT]
> <P>Because Microsoft BizTalk Server uses the underlying functionality of the .NET Framework, the results produced by some of the <STRONG>Conversion</STRONG> functoids vary from the equivalent functoids in earlier versions of BizTalk Server. For example, in earlier versions of BizTalk Mapper an input value of -20 to the <STRONG>Hexadecimal</STRONG> functoid resulted in an output of FFEC. In this version, the same input value of -20 results in an output of FFFFFFEC. You should test your maps thoroughly to ensure that you are getting the results you expect.</P>



For conceptual information about **Conversion** functoids, see [Conversion Functoids](https://msdn.microsoft.com/library/aa547311\(v=bts.80\)).

The following table shows the functoids in the **Conversion** category.

<table>
<thead>
<tr class="header">
<th>Conversion functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa578043.f5666aab-3a0e-4b89-b99c-2290a736373d(BTS.80).jpeg" /> <a href="ascii-to-character-functoid.md">ASCII to Character</a></td>
<td>Determines the character equivalent of a value interpreted as ASCII.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561886.39dfce53-76e8-47ed-a858-fb7b9d626dcf(BTS.80).jpeg" /> <a href="character-to-ascii-functoid.md">Character to ASCII</a></td>
<td>Determines the ASCII equivalent of the specified character.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa578422.898fb4dd-8e16-480c-8ada-aabfe1f196d9(BTS.80).jpeg" /> <a href="hexadecimal-functoid.md">Hexadecimal</a></td>
<td>Converts a decimal number to its hexadecimal equivalent.</td>
</tr>
<tr class="even">
<td><img src="images/Aa547877.67ce9c32-e259-4a34-88f3-34869443b869(BTS.80).jpeg" /> <a href="octal-functoid.md">Octal</a></td>
<td>Converts a decimal number to its octal equivalent.</td>
</tr>
</tbody>
</table>


## See Also

[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

