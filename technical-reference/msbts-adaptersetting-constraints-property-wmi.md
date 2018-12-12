---
title: MSBTS_AdapterSetting.Constraints Property (WMI)
TOCTitle: MSBTS_AdapterSetting.Constraints Property (WMI)
ms:assetid: 13dc7518-34d3-4e67-abfa-dd7151cc1537
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547628(v=BTS.80)
ms:contentKeyID: 51526355
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting.Constraints Property (WMI)

 

Gets or sets a bitmap with the constraints of the adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
uint32 Constraints;  
```

## Remarks

This property is read-only.

The following table describes the effect of each constraint bit when it is ON:

<table>
<thead>
<tr class="header">
<th>Description</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1</td>
<td>Indicates that the adapter supports receiving messages.</td>
</tr>
<tr class="even">
<td>2</td>
<td>Indicates that the adapter supports sending of messages.</td>
</tr>
<tr class="odd">
<td>8</td>
<td>Indicates which type of hosts can be receive handlers of the adapter. If bit is ON, then only In-Process hosts can be receive handlers of the adapter. If bit is OFF, then only Isolated hosts can be receive handlers of the adapter. This constraint only applies to the receive side. Send handlers are always created with In-Process hosts according to the BizTalk architecture.</td>
</tr>
<tr class="even">
<td>128</td>
<td>Indicates that the adapter supports request-response message exchanges.</td>
</tr>
<tr class="odd">
<td>256</td>
<td>Indicates that the adapter supports solicit-response message exchanges.</td>
</tr>
<tr class="even">
<td>1024</td>
<td>Indicates that the adapter uses the Adapter Framework user interface for send handler configuration.</td>
</tr>
<tr class="odd">
<td>2048</td>
<td>Indicates that the adapter uses adapter framework user interface for receive handler configuration.</td>
</tr>
<tr class="even">
<td>4096</td>
<td>Indicates that the adapter uses adapter framework user interface for receive location configuration.</td>
</tr>
<tr class="odd">
<td>8192</td>
<td>Indicates that the adapter uses adapter framework user interface for send port configuration.</td>
</tr>
<tr class="even">
<td>16384</td>
<td>Indicates that the adapter supports ordered delivery of messages.</td>
</tr>
<tr class="odd">
<td>32768</td>
<td>Indicates that the transmitter component of the adapter will be initialized when the BizTalk runtime service (host instance) starts instead of when the first message is sent.</td>
</tr>
<tr class="even">
<td>65536</td>
<td>Indicates that adapter supports running only in 32bit hosts.</td>
</tr>
</tbody>
</table>


The following table contains the constraints for the native adapters:

<table>
<thead>
<tr class="header">
<th>Adapter</th>
<th>Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>FILE</td>
<td>11</td>
</tr>
<tr class="even">
<td>FTP</td>
<td>80907</td>
</tr>
<tr class="odd">
<td>HTTP</td>
<td>387</td>
</tr>
<tr class="even">
<td>BizTalk Message Queuing</td>
<td>13579</td>
</tr>
<tr class="odd">
<td>SMTP</td>
<td>2</td>
</tr>
<tr class="even">
<td>SOAP</td>
<td>899</td>
</tr>
<tr class="odd">
<td>SQL</td>
<td>81163</td>
</tr>
<tr class="even">
<td>MQ Series</td>
<td>15627</td>
</tr>
<tr class="odd">
<td>POP3</td>
<td>71689</td>
</tr>
<tr class="even">
<td>Windows Sharepoint Services</td>
<td>15371</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

