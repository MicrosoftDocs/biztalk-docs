---
title: "MsSna_PrintSessionAppc Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5123f2cd-ca65-421c-96c3-b5b1c22f407b
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_PrintSessionAppc Class
Extends a print session. Uses APPC LU 6.2 protocols to communicate with the host.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PrintSessionAppc : MsSna_PrintSession  
{  
   String LocalLUAlias;  
   String RemoteLUAlias;  
   String RemoteFQName;  
   sint16 Remote;  
   String Mode;  
   String UserId;  
   String Password;  
   String AS400Device;  
   sint16 System36;  
   sint16 HostPrintTransform;  
   sint16 DeviceType;  
   String FontId;  
   String MsgQName;  
   String MsgLibName;  
   String PrinterName;  
   sint16 PaperSrc1;  
   sint16 PaperSrc2;  
   sint16 CodePage899;  
   String SpecialObjName;  
   String SpecialLibName;  
};  
```  
  
#### Parameters  
 **LocalLUAlias**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The local LU alias to be used for this print session. Valid only when a **RemoteLUAlias** is provided.  
  
 **RemoteLUAlias**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The remote LU alias. Valid only if a fully qualified name is not provided.  
  
 **RemoteFQName**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(17)</strong>Access Type: Read/Write  
  
 The remote LU fully qualified name. Valid only if **RemoteLUAlias** and **LocalLUAlias** are not provided.  
  
 **Remote**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that specifies what type of connection to use: either a remote APPC LU alias or a fully qualified name. The following table describes the possible values for **Remote**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Alias|  
|1|Fully qualified name|  
  
 **Mode**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The name of the mode to use. The default mode name is QPCSUPP.  
  
 **UserId**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(10)</strong>Access Type: Read/Write  
  
 The remote user name.  
  
 **Password**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The remote password.  
  
 **AS400Device**  
 Data Type: **String** Qualifiers: **MAXLEN(10), TOUPPERCASE** Access Type: Read/Write  
  
 The name for the AS/400 printer device. **AS400Device** should be a descriptive name that distinguishes different printers on the network.  
  
 **System36**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates whether the remote system is an AS/400 or a System/36. The following table describes the possible values for **System36**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|AS400|  
|1|System/36|  
  
 **HostPrintTransform**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates whether Host Print Transform (HPT) will be used. The following table describes the possible values for **HostPrintTransform**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|FALSE|  
|1|TRUE|  
  
 **DeviceType**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The print device for Host Print Transform. The following table describes the possible values for **DeviceType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|5224|  
|1|3812|  
  
 The default value for **DeviceType** is 5224.  
  
 **FontId**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 A font, which should be used instead of the default.  
  
 **MsgQName**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The qualified name of the message queue to which operational messages for this device are sent.  
  
 **MsgLibName**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The name of the library in which the message queue is located.  
  
 **PrinterName**  
 Data Type: **TOUPPERCASE** Access Type: Read/Write  
  
 The printer type to be used with Host Print Transform. For more information on the possible values for **PrinterName**, see the **Remarks** section.  
  
 **PaperSrc1**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The type of paper used in paper source 1. The following table describes the possible values for **PaperSrc1**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Default|  
|1|Letter (8.5 x 11 inches)|  
|2|Legal (8.5 x 14 inches)|  
|3|Executive (7.25 x 10.5 inches)|  
|4|A4 (210 x 297 mm)|  
|5|A5 (148 x 210 mm)|  
|6|B5 (182 x 257 mm)|  
|7|Continuous Form (8.0 inches)|  
|8|Continuous Form (13.2 inches)|  
|9|None|  
  
 **PaperSrc2**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The type of paper used in paper source 2. The following table describes the possible values for **PaperSrc2**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Default|  
|1|Letter (8.5 x 11 inches)|  
|2|Legal (8.5 x 14 inches)|  
|3|Executive (7.25 x 10.5 inches)|  
|4|A4 (210 x 297 mm)|  
|5|A5 (148 x 210 mm)|  
|6|B5 (182 x 257 mm)|  
|7|Continuous Form (8.0 inches)|  
|8|Continuous Form (13.2 inches)|  
|9|None|  
  
 **CodePage899**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates whether code page 899 is used. The following table describes the possible values of **CodePage899**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|FALSE|  
|1|TRUE|  
  
 **SpecialObjName**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The name of the special object.  
  
 **SpecialLibName**  
 Data Type: **String** Qualifiers: **MAXLEN(10)** Access Type: Read/Write  
  
 The name of the special library.  
  
## Remarks  
 The following table describes the possible values for **PrinterName**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|*IBM2380|  
|1|*IBM2381|  
|2|*IBM2390|  
|3|*IBM2391|  
|4|*IBM3812|  
|5|*IBM3816|  
|6|*IBM3912HP|  
|7|*IBM3916HP|  
|8|*IBM39302|  
|9|*IBM39303|  
|10|*IBM4019|  
|11|*IBM4019HP|  
|12|*IBM4029|  
|13|*IBM4029HP|  
|14|*IBM4037|  
|15|*IBM4037HP|  
|16|*IBM4070|  
|17|*IBM4070EP|  
|18|*IBM42011|  
|19|*IBM42012|  
|20|*IBM42013|  
|21|*IBM42021|  
|22|*IBM42022|  
|23|*IBM42023|  
|24|*IBM42071|  
|25|*IBM42072|  
|26|*IBM42081|  
|27|*IBM4212|  
|28|*IBM4216|  
|29|*IBM4226|  
|30|*IBM4230|  
|31|*IBM4232|  
|32|*IBM47121|  
|33|*IBM47122|  
|34|*IBM47221|  
|35|*IBM47222|  
|36|*IBM4770|  
|37|*IBM5152|  
|38|*IBM5210|  
|39|*IBM5202|  
|40|*IBM5204|  
|41|*IBM5216|  
|42|*IBM6408|  
|43|*IBM6412|  
|44|*CPQPM15|  
|45|*CPQPM20|  
|46|*HPII|  
|47|*HPIID|  
|48|*HPIIP|  
|49|*HPIIID|  
|50|*HPIIIP|  
|51|*HPIIISI|  
|52|*HP4|  
|53|*HP500|  
|54|*HP550C|  
|55|*HP560C|  
|56|*HPPAINT|  
|57|*EPAP2250|  
|58|*EPAP3250|  
|59|*EPAP5000|  
|60|*EPAP5500|  
|61|*EPDFX5000|  
|62|*EPDFX8000|  
|63|*EPDFX850|  
|64|*EPDFX870|  
|65|*EPDFX1170|  
|66|*EPLQ570|  
|67|*EPLQ860|  
|68|*EPLQ870|  
|69|*EPLQ1070|  
|70|*EPLQ1170|  
|71|*EPLX810|  
|72|*EPLQ510|  
|73|*EPLQ2550|  
|74|*EPSQ870|  
|75|*EPSQ1170|  
|76|*EPEPL7000|  
|77|*EPEPL8000|  
|78|*OKI320IBM|  
|79|*OKI321IBM|  
|80|*OKI390IBM|  
|81|*OKI393IBM|  
|82|*OKI590IBM|  
|83|*OKI591IBM|  
|84|*OKI400|  
|85|*OKI800|  
|86|*OKI810|  
|87|*OKI820|  
|88|*OKI3410|  
|89|*NECP2|  
|90|*NEC2200|  
|91|*NECP2200XE|  
|92|*NECP5200|  
|93|*NECP5300|  
|94|*NECP6200|  
|95|*NECP6300|  
|96|*PAN1123EP|  
|97|*PAN1124|  
|98|*PAN1124IEP|  
|99|*PAN1180EP|  
|100|*PAN1180IEP|  
|101|*PAN1191|  
|102|*PAN1624EP|  
|103|*PAN1654EP|  
|104|*PAN1695EP|  
|105|*PAN2123EP|  
|106|*PAN2124|  
|107|*PAN2180|  
|108|*PAN2624EP|  
|109|*PAN4410|  
|110|*PAN4420|  
|111|*PAN4430|  
|112|*PAN4450IHP|  
|113|*PAN4451HP|  
|114|*XRX4215MRP|  
|115|*XRX4219MRP|  
|116|*XRX4220MRP|  
|117|*XRX4235|  
|118|*XRX4700II|  
|119|*WSCST|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)