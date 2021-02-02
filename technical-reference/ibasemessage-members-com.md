---
description: "Learn more about: IBaseMessage Members (COM)"
title: IBaseMessage Members (COM)
TOCTitle: IBaseMessage Members (COM)
ms:assetid: 0bf31a14-56e0-4ba1-ba55-033e34735ad5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547254(v=BTS.80)
ms:contentKeyID: 51526155
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# IBaseMessage Members (COM)

 

[IBaseMessage overview](ibasemessage-interface-com.md)

## Public Properties

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-bodypart-property-com.md">BodyPart</a></td>
<td>Gets the body part, or main part, of the message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-bodypartname-property-com.md">BodyPartName</a></td>
<td>Gets the name of the body part, or main part, of the message.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-context-property-com.md">Context</a></td>
<td>Represents the message context.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-ismutable-property-com.md">IsMutable</a></td>
<td>Gets a value indicating whether the message context can be changed by components during processing.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-messageid-property-com.md">MessageID</a></td>
<td>Gets the unique message ID for the message and binds all the message parts together.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" /> <a href="ibasemessage-partcount-property-com.md">PartCount</a></td>
<td>Gets the total number of parts in the message.</td>
</tr>
</tbody>
</table>


## Public Methods

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-addpart-method-com.md">AddPart</a></td>
<td>Adds a part to the message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-geterrorinfo-method-com.md">GetErrorInfo</a></td>
<td>Gets the exception that caused the error.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-getpart-method-com.md">GetPart</a></td>
<td>Accesses the message parts.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-getpartbyindex-method-com.md">GetPartByIndex</a></td>
<td>Retrieves a part and its name by supplying the part index.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-getsize-method-com.md">GetSize</a></td>
<td>Gets the size of the message.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-removepart-method-com.md">RemovePart</a></td>
<td>Removes a part from the message.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" /> <a href="ibasemessage-seterrorinfo-method-com.md">SetErrorInfo</a></td>
<td>Sets the error information.</td>
</tr>
</tbody>
</table>


## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)

