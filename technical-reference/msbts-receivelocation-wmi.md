---
title: MSBTS_ReceiveLocation (WMI)
TOCTitle: MSBTS_ReceiveLocation (WMI)
ms:assetid: f75bd1ce-1bf5-4707-9b8e-55377c2538a1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561991(v=BTS.80)
ms:contentKeyID: 51533505
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation (WMI)

 

Represents an individual receive location defined by Microsoft BizTalk Server.


> [!WARNING]
> <P>Certificates must be installed on the box for the MSBTS_ReceiveLocation class to work. The only way to create receive locations without certificates is to use the <A href="https://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx">Microsoft.BizTalk.ExplorerOM</A>APIs.</P>



## Declaration

```C#
class MSBTS_ReceiveLocation : MSBTS_Setting  
```

## Members

**MSBTS\_ReceiveLocation** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-receivelocation-activestartdt-property-wmi.md">MSBTS_ReceiveLocation.ActiveStartDT Property (WMI)</a></td>
<td>Contains the date when the receive location should activate.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-activestopdt-property-wmi.md">MSBTS_ReceiveLocation.ActiveStopDT Property (WMI)</a></td>
<td>Contains the date when the receive location should deactivate.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-adaptername-property-wmi.md">MSBTS_ReceiveLocation.AdapterName Property (WMI)</a></td>
<td>Contains the name of the adapter used by the receive location.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/p/?linkid=20246">http://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-customcfg-property-wmi.md">MSBTS_ReceiveLocation.CustomCfg Property (WMI)</a></td>
<td>Contains the adapter-specific configuration in XML format.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/p/?linkid=20246">http://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-encryptioncert-wmi.md">MSBTS_ReceiveLocation.EncryptionCert (WMI)</a></td>
<td>Contains the Name of the certificate used for outbound encryption.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-hostname-property-wmi.md">MSBTS_ReceiveLocation.HostName Property (WMI)</a></td>
<td>Contains the name of the receive handler used by the receive location.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-inboundaddressableurl-property-wmi.md">MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI)</a></td>
<td>Contains a URL that can be used by external parties to send documents to the receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-inboundtransporturl-property-wmi.md">MSBTS_ReceiveLocation.InboundTransportURL Property (WMI)</a></td>
<td>Contains an adapter-specific URL which the given instance of the receive location is listening to.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-isdisabled-property-wmi.md">MSBTS_ReceiveLocation.IsDisabled Property (WMI)</a></td>
<td>Enables or disables a receive function.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-isprimary-property-wmi.md">MSBTS_ReceiveLocation.IsPrimary Property (WMI)</a></td>
<td>Specifies a primary receive function to use for correlation.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-mgmtdbnameoverride-property-wmi.md">MSBTS_ReceiveLocation.MgmtDbNameOverride Property (WMI)</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-mgmtdbserveroverride-property-wmi.md">MSBTS_ReceiveLocation.MgmtDbServerOverride Property (WMI)</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-name-property-wmi.md">MSBTS_ReceiveLocation.Name Property (WMI)</a></td>
<td>Contains the name of the receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-operatingwindowenabled-wmi.md">MSBTS_ReceiveLocation.OperatingWindowEnabled (WMI)</a></td>
<td>Enables or disables a service window, which is defined by the <strong>SrvWinStartDT</strong> and <strong>SrvWinStopDT</strong> properties.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-pipelinename-property-wmi.md">MSBTS_ReceiveLocation.PipelineName Property (WMI)</a></td>
<td>Contains the name of the pipeline that will process the document before the document is submitted to the MessageBox database.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-receiveportname-property-wmi.md">MSBTS_ReceiveLocation.ReceivePortName Property (WMI)</a></td>
<td>Contains the name of the receive port used by the receive location.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-sendpipeline-wmi.md">MSBTS_ReceiveLocation.SendPipeline (WMI)</a></td>
<td>Contains the name of the send pipeline used by the receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-sendpipelinedata-wmi.md">MSBTS_ReceiveLocation.SendPipelineData (WMI)</a></td>
<td>Contains the custom configuration data for the SendPipeline in XML format.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/p/?linkid=20246">http://go.microsoft.com/fwlink/p/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-srvwinstartdt-property-wmi.md">MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)</a></td>
<td>Contains the start time of a service window when the receive location should activate.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-srvwinstopdt-property-wmi.md">MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)</a></td>
<td>Contains the end time of a service window when the receive location should deactivate.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-startdateenabled-wmi.md">MSBTS_ReceiveLocation.StartDateEnabled (WMI)</a></td>
<td>Enables or disables the active start date specified by <strong>ActiveStartDT</strong> property.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-stopdateenabled-wmi.md">MSBTS_ReceiveLocation.StopDateEnabled (WMI)</a></td>
<td>Enables or disables the active stop date specified by <strong>ActiveStopDT</strong> property.</td>
</tr>
</tbody>
</table>


**MSBTS\_ReceiveLocation** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-receivelocation-disable-method-wmi.md">MSBTS_ReceiveLocation.Disable Method (WMI)</a></td>
<td>Disables a receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocation-enable-method-wmi.md">MSBTS_ReceiveLocation.Enable Method (WMI)</a></td>
<td>Enables a receive location.</td>
</tr>
</tbody>
</table>


## Remarks


> [!NOTE]
> <P>If a send port or receive location is updated using the BizTalk Explorer object model or a WMI script, the Receive Port Properties and Send Port Properties property pages in BizTalk Explorer will display an incorrect Address (URI). The Address (URI) used internally is the Address (URI) set by the script, so the script works as expected. To update the property pages to display the correct Address (URI), update the Address (URI) field in BizTalk Explorer with the new value.</P>




> [!NOTE]
> <P>This class wraps the managed <STRONG>Microsoft.BizTalk.ExplorerOM.ReceiveLocation</STRONG> class.</P>



## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

