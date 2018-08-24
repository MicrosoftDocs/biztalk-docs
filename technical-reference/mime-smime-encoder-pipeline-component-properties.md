---
title: MIME-SMIME Encoder Pipeline Component Properties
TOCTitle: MIME-SMIME Encoder Pipeline Component Properties
ms:assetid: b5efd9df-c30c-46db-ab59-2dd1e9fe5224
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578240(v=BTS.80)
ms:contentKeyID: 51530732
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.MIME_SMIME_Encoder
---

# MIME-SMIME Encoder Pipeline Component Properties

 

Use the MIME/SMIME encoder pipeline component to provide MIME encoding functionality to messages.

The MIME/SMIME encoder pipeline component is intended for use in the Encode stage of a Send pipeline.

The properties of the MIME/SMIME encoder pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable MIME/SMIME encoder pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Add signing certification to message</strong></td>
<td>Select whether to add the signing certificate to the signed message, if the <strong>Signature Type</strong> property is not NoSign, by setting the <strong>Add signing cert to the message</strong> property.<br />
<br />
Default Value: True</td>
</tr>
<tr class="even">
<td><strong>Check Revocation list</strong></td>
<td>Indicate whether to check the Certificate Revocation List while processing an SMIME message.<br />
<br />
Default Value: True</td>
</tr>
<tr class="odd">
<td><strong>Content transfer encoding</strong></td>
<td>Indicate the encoding format.<br />
<br />
Options: Base64, QuotedPrintable, SevenBit, EightBit, Binary, and UUEncode.<br />
<br />
Default Value: Base64</td>
</tr>
<tr class="even">
<td><strong>Enable encryption</strong></td>
<td>Set this property to True if you need to encrypt the outgoing message. If this option is enabled, then the user can select the encryption algorithm to use by setting the <strong>Encryption algorithm</strong> property. For message encryption, the MIME/SMIME pipeline component uses the public key certificate that is associated with a send port in BizTalk Explorer.<br />
<br />
Default Value: False</td>
</tr>
<tr class="odd">
<td><strong>Encryption algorithm</strong></td>
<td>Define the encryption algorithm.<br />
<br />
This property can only be set if Enable Encryption is set to True.<br />
<br />
Options: DES3, DES, RC2.<br />
<br />
Default Value: DES3</td>
</tr>
<tr class="even">
<td><strong>Send body part as attachment</strong></td>
<td>Set this property to True if you want to send the body party of BizTalk message as a MIME attachment.<br />
<br />
Default Value: False</td>
</tr>
<tr class="odd">
<td><strong>Signature type</strong></td>
<td>Select a signing format by setting this property, if you need to sign the outgoing message. This property has three values:<br />
<br />
- NoSign. The message will not be signed.<br />
- ClearSign. The signature will be appended to the messages.<br />
- BlobSign. The signature will be appended to the message and the message will be encoded. For message signing, the MIME/SMIME component uses the private key client certificate that is associated with the BizTalk group in the BizTalk Server Administration Console.<br />
<br />
Default Value: NoSign</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/en-us/library/aa578392\(v=bts.80\))  
[How to Configure the MIME-SMIME Encoder Pipeline Component](https://msdn.microsoft.com/en-us/library/aa561432\(v=bts.80\))  
[MIME-SMIME Encoder Pipeline Component](https://msdn.microsoft.com/en-us/library/aa559633\(v=bts.80\))

