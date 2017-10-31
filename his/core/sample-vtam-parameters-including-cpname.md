---
title: "Sample VTAM Parameters Including CPNAME1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8c02ab9-b64d-4fa7-90c9-9d6e80d74b32
caps.latest.revision: 3
---
# Sample VTAM Parameters Including CPNAME
The following is a sample of VTAM parameters that might be used for a Token Ring connection to an IBM 9370 host, when identification of the computer running [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] is based on Control Point Name (CPNAME). For this configuration, Format XIDs must be exchanged.  
  
 In the PU definition, IDBLK, IDNUM, MACADDR, and SAPADDR are not used. For this configuration to work on [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)], the Remote Node ID, Remote Network Name, and Remote Control Point Name should all be left blank. Additionally, the Local Node ID can be left at the default value (because it is not used).  
  
 In this sample, the underlined values correspond to values specified in [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] Manager.  
  
```  
R01100   PORT CUADDR=100,<U>MACADDR=400040004001</U>,LANCON=(5,2),         X  
              MAXDATA=2012,MAXSTN=52,SAPADDR=04  
  
SERVER01 PU   ADDR=C1,<U>CPNAME=SERVER01</U>,ANS=CONTINUE,                 X  
              <U>MAXDATA=0265</U>,MAXOUT=7,MAXPATH=7,                      X  
              PACING=0,VPACING=0,SSCPFM=USSSCS,                     X  
              LANACK=(0,0),LANCON=(5,2),LANINACT=4.8,               X  
              LANRESP=(5,2),LANSDWDW=(7,1),LANSW=YES,               X  
              USSTAB=MSUSSTAB,DLOGMOD=D4C32792,                     X  
              PUTYPE=2,DISCNT=(NO),ISTATUS=ACTIVE  
  
T0110002 LU   <U>LOCADDR=002</U>     
T0110003 LU   <U>LOCADDR=003</U>  
T0110004 LU   <U>LOCADDR=004</U>  
T0110005 LU   <U>LOCADDR=005</U>  
P0110006 LU   <U>LOCADDR=006</U>,DLOGMOD=LU33286S  
T0110007 LU   <U>LOCADDR=007</U>  
T0110008 LU   <U>LOCADDR=008</U>  
  
```  
  
 The following table shows the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] parameters and values that correspond to the sample VTAM parameters.  
  
> [!NOTE]
>  For this example, it is assumed that the local Network Name configured for the Host Integration Server matches the NETID parameter in the VTAM Start command for the local SSCP. (The VTAM system to which Host Integration Server is attached.)  
  
|Host Integration Server parameter|Sample value|VTAM parameter|  
|---------------------------------------|------------------|--------------------|  
|Remote Network Address|400040004001|MACADDR= parameter in the PORT definition|  
|Local Control Point Name (for the server)|SERVER01|CPNAME= parameter in the PU definition|  
|Max BTU Length|265|MAXDATA= parameter in the PU definition (set Max BTU Length less than or equal to MAXDATA)|  
|LU Numbers|2 through 8|LOCADDR= parameter in the LU definitions|  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters.md)