---
title: "Sample CICS Configuration Screens for Use with APPC2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4936e582-d258-461b-8f79-e39961b532f1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sample CICS Configuration Screens for Use with APPC
The following series of screens show how CICS could be configured for independent Advanced Program-to-Program Communications (APPC) through VTAM. In the first screen, the underlined values correspond to values specified in SNA Server Manager.  
  
```  
OVERTYPE TO MODIFY                    CICS RELEASE = 0330  
 CEDA  ALter  
  <U>Sessions       : LOCLU1</U>  
  Group          : VER3AAAA  
  DEscription  ==> VERSION 3 LU 6.2 SESSION ENTRY  
 SESSION IDENTIFIERS  
  Connection   ==> CON1  
  SESSName     ==>  
  NETnameq     ==>  
  <U>MOdename     ==> APPCMODE</U>  
 SESSION PROPERTIES  
  Protocol     ==> Appc                Appc | Lu61  
  <U>MAximum      ==> 250 , 125</U>           0-999  
  RECEIVEPfx   ==>  
  RECEIVECount ==>                     1-999  
  SENDPfx      ==>  
  SENDCount    ==>                     1-999  
  <U>SENDSize     ==> 00521</U>               1-30720  
  <U>RECEIVESize  ==> 00521</U>               1-30720  
  
                                            <U>APPLID=CICSLU</U>  
PF 1 HELP 2 COM 3 END   6 CRSR 7 SBH 8 SFH 9 MSG 10 SB 11 SF 12 CNCL  
  
```  
  
 The following table shows [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters and values that correspond to the preceding sample CICS parameters.  
  
|Host Integration Server parameter|Sample value|CICS parameter|  
|---------------------------------------|------------------|--------------------|  
|LU Name for local APPC LU|LOCLU1|Sessions|  
|Mode name|APPCMODE|Modename|  
|Parallel Session Limit in the mode|250|Maximum|  
|Partner Min Contention Winner Limit in the mode|125|Maximum|  
|Max Receive RU Size in the mode|00521|SENDSize|  
|Max Send RU Size in the mode|00521|RECEIVESize|  
|LU Name for remote APPC LU|CICSLU|APPLID|  
  
 In the sample CICS screen, the parameter called Maximum has two values, 250 and 125, separated by commas. The first value (250) is the parallel session limit. The second value (125) is the host minimum contention winner limit. On Host Integration Server, this corresponds to Partner Min Contention Winner Limit in the mode. In addition, because the host is the contention winner on 125 sessions (out of a total of 250), Host Integration Server should be configured as the contention winner on the remaining 125 sessions. In this case, Host Integration Server mode would have the following values:  
  
- Parallel Session Limit 250  
  
- Minimum Contention Winner Limit 125  
  
- Partner Min Contention Winner Limit 125  
  
- Automatic Activation Limit 0  
  
  The remaining screens in this section show more information about how CICS could be configured for independent APPC through VTAM.  
  
```  
OVERTYPE TO MODIFY                    CICS RELEASE = 0330  
 CEDA  ALter  
 SESSION PROPERTIES  
  SESSPriority ==> 000                 0-255  
  Transaction    :  
 OPERATOR DEFAULTS  
  OPERId         :  
  OPERPriority   : 000                 0-255  
  OPERRsl        : 0                              0-24,...  
  OPERSecurity   : 1                              1-64,...  
 PRESET SECURITY  
  USERId       ==>  
 OPERATIONAL PROPERTIES  
  Autoconnect  ==> Yes                 No | Yes | All  
  INservice      :                     No | Yes  
  Buildchain   ==> Yes                 Yes | No  
  USERArealen  ==> 000                 0-255  
  IOarealen    ==> 00000 , 00000       0-32767  
  RELreq       ==> No                  No | Yes  
  DIscreq      ==> No                  No | Yes  
  NEPclass     ==> 000                 0-255  
 RECOVERY  
  RECOVOption  ==> Sysdefault  Sysdefault | Clearconv   
                               | Releasesess | Uncondrel  
                               | None  
  RECOVNotify  ==> None       None | Message | Transaction  
  
                                            APPLID=CICSLU  
PF 1 HELP 2 COM 3 END   6 CRSR 7 SBH 8 SFH 9 MSG 10 SB 11 SF 12 CNCL  
  
```  
  
 In the following screen, the underlined value corresponds to the LU Name of the local APPC LU in Host Integration Server.  
  
```  
OVERTYPE TO MODIFY                    CICS RELEASE = 0330  
 CEDA  ALter  
  Connection     : CON1  
  Group          : VER3AAAA  
  DEscription  ==> VERSION 3  LU 6.2 DEFINITION  
 CONNECTION IDENTIFIERS  
  <U>Netname      ==> LOCLU1</U>  
  INDsys       ==>  
 REMOTE ATTRIBUTES  
  REMOTESystem ==>  
  REMOTEName   ==>  
 CONNECTION PROPERTIES  
  ACcessmethod ==> Vtam                Vtam | IRc   
                                       |INdirect | Xm  
  Protocol     ==> Appc                Appc | Lu61  
  SInglesess   ==> No                  No | Yes  
  DAtastream   ==> User                User | 3270 | SCs   
                                       | STrfield | Lms  
  RECordformat ==> U                   U | Vb  
 OPERATIONAL PROPERTIES  
  AUtoconnect  ==> Yes                 No | Yes | All  
  INService    ==> Yes                 Yes | No  
 SECURITY  
  SEcurityname ==>  
  ATtachsec    ==> Verify              Local | Identify   
                                       | Verify | Persistent  
                                       | Mixidpe  
  BINDPassword ==>                     PASSWORD SPECIFIED  
  BINDSecurity ==> No                  No | Yes  
  
                                            APPLID=CICSLU  
PF 1 HELP 2 COM 3 END   6 CRSR 7 SBH 8 SFH 9 MSG 10 SB 11 SF 12 CNCL  
  
```  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)