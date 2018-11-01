---
title: Functoid Reference
TOCTitle: Functoid Reference
ms:assetid: ed56b236-3663-4a20-a2ea-14e4a4492bf8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561783(v=BTS.80)
ms:contentKeyID: 51533249
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Functoid Reference

 

BizTalk Mapper provides an extensive set of functoids that can be used in maps to perform a variety of operations on data that is being transformed from a source instance message to a destination instance message. This section provides reference information about the BizTalk Mapper functoids.


> [!IMPORTANT]
> <P>Because Microsoft BizTalk Server uses the underlying functionality of the .NET Framework, the results produced by some functoids vary from the equivalent functoids in previous versions of BizTalk Server. You should test your maps thoroughly to ensure you are getting the results you expect.</P>




> [!NOTE]
> <P>Whenever an input parameter to a functoid is not valid, a default value is passed to the functoid in its place. For numeric input parameters, the default value is zero (0). For all other input parameters, the default value is blank.</P>
> <P>The above doesn’t apply to all the functoids. For instance, the default value is applied to functoids like MathAdd, but not applied to functoids like MathSqrt or GetCummulativeAvg.</P>




> [!NOTE]
> <P>If a functoid connects to a <STRONG>Record</STRONG> node in the destination schema, that node should have its <STRONG>Mixed</STRONG> property set to <STRONG>True</STRONG> for the output document to be valid against the schema. This is because the functoid writes data into the corresponding element. The <STRONG>Mixed</STRONG> property may be set to <STRONG>False</STRONG> if the <STRONG>Content Type</STRONG> is <STRONG>SimpleContent</STRONG>.</P>



The following table shows the categories into which these functoids have been divided.

<table>
<thead>
<tr class="header">
<th>Functoid Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="advanced-functoids-reference.md">Advanced Functoids Reference</a></td>
<td>Use <strong>Advanced</strong> functoids to create various types of data manipulation, such as implementing custom script, value mapping, and managing and extracting data from looping records.</td>
</tr>
<tr class="even">
<td><a href="conversion-functoids-reference.md">Conversion Functoids Reference</a></td>
<td>Use <strong>Conversion</strong> functoids to convert characters to and from their numeric representation, and to convert numbers from one base to another.</td>
</tr>
<tr class="odd">
<td><a href="cumulative-functoids-reference.md">Cumulative Functoids Reference</a></td>
<td>Use <strong>Cumulative</strong> functoids to perform various types of accumulation operations for values that occur multiple times within an instance message.</td>
</tr>
<tr class="even">
<td><a href="database-functoids-reference.md">Database Functoids Reference</a></td>
<td>Use <strong>Database</strong> functoids to look up data from a database and to perform simple cross-referencing operations (sometimes called ID mapping).</td>
</tr>
<tr class="odd">
<td><a href="date-and-time-functoids-reference.md">Date and Time Functoids Reference</a></td>
<td>Use <strong>Date and Time</strong> functoids to add date, time, date and time, or add days to a specified date, in output data.</td>
</tr>
<tr class="even">
<td><a href="logical-functoids-reference.md">Logical Functoids Reference</a></td>
<td>Use <strong>Logical</strong> functoids to conditionally control the behavior of other functoids and to determine whether particular output data is created.</td>
</tr>
<tr class="odd">
<td><a href="mathematical-functoids-reference.md">Mathematical Functoids Reference</a></td>
<td>Use <strong>Mathematical</strong> functoids to perform specific numeric calculations such as addition, multiplication, and division.</td>
</tr>
<tr class="even">
<td><a href="scientific-functoids-reference.md">Scientific Functoids Reference</a></td>
<td>Use <strong>Scientific</strong> functoids to perform specific scientific calculations such as logarithmic, exponential, and trigonometric functions.</td>
</tr>
<tr class="odd">
<td><a href="string-functoids-reference.md">String Functoids Reference</a></td>
<td>Use the <strong>String</strong> functoids to manipulate data strings by using well-known string functions such as concatenation, length, find, and trim.</td>
</tr>
</tbody>
</table>

