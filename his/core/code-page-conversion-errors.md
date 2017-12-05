---
title: "Code Page Conversion Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e7f6ab3-dbca-4acb-9d7a-fa30aea6f44f
caps.latest.revision: 3
---
# Code Page Conversion Errors
IBM host systems are designed to utilize Extended Binary Coded Decimal Interchange Code (EBCDIC) when handling character string data types. Windows computers are designed to utilize ANSI or UNICODE. The HIS SNANLS API handles conversion from EBCDIC to and from UNICODE, and UNICODE to and from ANSI. When using the HIS data providers, you may encounter code page conversion errors. This topic contains the following sections:  
  
 [OLE DB Provider for DB2](../core/code-page-conversion-errors.md#oledb)  
  
 [OLE DB Provider for AS/400 and VSAM](../core/code-page-conversion-errors.md#oleasvs)  
  
 [ADO.NET Provider for DB2](../core/code-page-conversion-errors.md#addb)  
  
 [ADO.NET Provider for Host Files](../core/code-page-conversion-errors.md#adhos)  
  
 [BizTalk Adapter for DB2](../core/code-page-conversion-errors.md#btdb)  
  
 [BizTalk Adapter for Host Files](../core/code-page-conversion-errors.md#bthost)  
  
 For more information on SNANLS, see [SNA Internationalization Programmer's Reference](../core/sna-internationalization-programmer-s-reference1.md) in the [Network Integration Programmer's Reference](../core/network-integration-programmer-s-reference1.md).  
  
 For more information on configuring code page conversion when using the data providers for DB2, see [Data Source Wizard (DB2)](../core/data-source-wizard-db2-1.md) and [Data Links (DB2)](../core/data-links-db2-1.md) in [Data Integration (Configuration)](../core/data-integration-configuration-1.md).  
  
 For more information on configuring code page conversion when using the data providers for host files, see [Data Source Wizard (Host Files)](../core/data-source-wizard-host-files-1.md) and [Data Links (Host Files)](../core/data-links-host-files.md) in [Data Integration (Configuration)](../core/data-integration-configuration-1.md).  
  
##  <a name="oledb"></a> OLE DB Provider for DB2  
  
##  <a name="oleasvs"></a> OLE DB Provider for AS/400 and VSAM  
 Character code conversions under the OLE DB Provider for AS/400 and VSAM are controlled by a hierarchy of parameters. When connecting to mainframes all of these parameters are controlled on the personal computer. However, when connecting to data sources on the midrange i5/OS computer, parameter settings on the i5/OS as well as parameter settings on the personal computer can be involved.  
  
 The character code set identifier (CCSID) used by the host for a data source can be specified in several locations. The Host CCSID setting used by the OLE DB provider must be set to match the CCSID actually used on the host; otherwise data loss will occur. Note that some i5/OS computers default to a CCSID of 937 rather than 37 for enabling double-byte character sets (DBCS).  
  
 The following table illustrates the separate hierarchy controlling the Host CCSID parameter on the SNA client and midrange i5/OS server.  
  
||||  
|-|-|-|  
|**SNA client**|**AS/400 host**|**Mainframe host**|  
|SNA OLE DB provider (defaults to U.S./Canada 37)|System (DSPSYSVAL, QCCSID)|None. Determined by the Data Description (HCD file) on the SNA Client.|  
|Data Source (the Host CCSID parameter in the Data Links file describing the Data Source)|User identifier (wrkusrprf)||  
|Data Description (HCD file)|Job (dspjob, crtjobd)||  
||File (dspfd, crtpf)||  
||Column (dspffd)||  
  
 **Specifying Host CCSID in the Host Column Description Files**  
  
 A Host CCSID attribute can be applied at the Data Description level. Each column in a host column description (HCD) file can have a Host CCSID attribute that determines how the character data in the column is to be converted. These attributes in the HCD file at the Data Description level should be configured using Host Files Designer.  
  
 The Host CCSID attribute at the column Data Description level can be any value and may be empty. A Host CCSID value at the Data Description level overrides the value specified at the Data Source and OLE DB provider levels. If the Host CCSID is blank, the value for Host CCSID defaults to the value at the Data Source level. If the Host CCSID attribute is set to 65535, no character conversion occurs (the data is treated as binary).  
  
 There is a Data Source parameter configurable using Data Links that affects whether binary data is considered as character data and is converted based on the Host CCSID setting. This **Process Binary As Character** parameter defaults to *false*. If this parameter is *false*, binary data is not treated as character (binary data is not affected by the Host CCSID setting). If this parameter is set to *true*, binary data is converted based on the Host CCSID setting. This parameter is configured for each Data Source using Data Links under the **All** tab of the **Data Links** dialog box.  
  
##  <a name="addb"></a> ADO.NET Provider for DB2  
  
##  <a name="adhos"></a> ADO.NET Provider for Host Files  
  
##  <a name="btdb"></a> BizTalk Adapter for DB2  
  
##  <a name="bthost"></a> BizTalk Adapter for Host Files  
  
## See Also  
 [Data Integration (Troubleshooting)](../core/data-integration-troubleshooting-1.md)