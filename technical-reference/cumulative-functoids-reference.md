---
description: "Learn more about: Cumulative Functoids Reference"
title: Cumulative Functoids Reference
TOCTitle: Cumulative Functoids Reference
ms:assetid: ee3b72df-92f3-4516-973a-c439eae1c150
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561799(v=BTS.80)
ms:contentKeyID: 51533245
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Cumulative Functoids Reference

 

Use **Cumulative** functoids to perform various types of accumulation operations for values that occur multiple times within an instance message. For example, you can use the **Cumulative Sum** functoid to provide the combined total for a value that occurs in multiple records within a specified scope in an instance message.

In Microsoft BizTalk Server, all **Cumulative** functoids accept two input parameters, the second of which is an optional scoping parameter that was not used in the **Cumulative** functoids in earlier versions of BizTalk Server. The two parameters are:

  - **Parameter 1:** The value to be accumulated. This value must be numeric for all **Cumulative** functoids other than the **Cumulative Concatenate** functoid, which expects a string value. You supply this value by creating a link between a **Field Attribute**, **Field Element**, or **Record** (with its **Mixed** property set to **True**) node that has an appropriate data type and the **Cumulative** functoid.
    

    > [!NOTE]
    > <P>If none of the ancestor <STRONG>Record</STRONG> nodes in the schema tree are repeating, using a <STRONG>Cumulative</STRONG> functoid is pointless.</P>



  - **Parameter 2:** The scope to which the value specified as the first parameter should be accumulated. This optional numeric value indicates how closely "related" the specified values in an instance message must be in order to participate in the accumulation, as follows:
    
      - The default value of zero (0) indicates that the element or attribute value, as indicated by its element or attribute name, should be accumulated over the entire instance message.
    
      - A scoping value of one (1) indicates that only element or attribute values that have the same parent element should be accumulated.
    
      - A scoping value of two (2) indicates that only element or attribute values that have the same grandparent element should be accumulated, and so on.


> [!NOTE]
> <P>All <STRONG>Cumulative</STRONG> functoids provide backward compatibility with Microsoft BizTalk Server 2000 and Microsoft BizTalk Server 2002, both of which required only one input parameter. They default to a scoping parameter of zero (0), meaning a scope of the entire instance message.</P>



For additional conceptual information about **Cumulative** functoids, including the scoping parameter, see [Cumulative Functoids](https://msdn.microsoft.com/library/aa561839\(v=bts.80\)).

The following table shows the functoids in the **Cumulative** category.

<table>
<thead>
<tr class="header">
<th>Cumulative functoid</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Aa578299.ab36f1e7-3341-464c-a171-f93bce223bbe(BTS.80).jpeg" /> <a href="cumulative-average-functoid.md">Cumulative Average</a></td>
<td>Calculates the accumulated average of a numeric value that recurs within corresponding instance messages.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561799.96cb173a-f7b9-4042-a525-1e1f7475d54e(BTS.80).jpeg" /> <a href="cumulative-concatenate-functoid.md">Cumulative Concatenate</a></td>
<td>Concatenates multiple instances of a string value that recurs within corresponding instance messages.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa561894.eafb0c35-4d1c-4454-a475-0a605a839e2f(BTS.80).jpeg" /> <a href="cumulative-maximum-functoid.md">Cumulative Maximum</a></td>
<td>Determines the maximum value of a numeric value that recurs within corresponding instance messages.</td>
</tr>
<tr class="even">
<td><img src="images/Aa561799.066f13a5-aa0c-4e9d-87ee-6667d9a3a39e(BTS.80).jpeg" /> <a href="cumulative-minimum-functoid.md">Cumulative Minimum</a></td>
<td>Determines the minimum value of a numeric value that recurs within corresponding instance messages.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa561799.a1343591-0bdc-48dd-929d-c9ddae9c5e86(BTS.80).jpeg" /> <a href="cumulative-sum-functoid.md">Cumulative Sum</a></td>
<td>Calculates the accumulated sum of a numeric value that recurs within corresponding instance messages.</td>
</tr>
</tbody>
</table>


## See Also

[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

