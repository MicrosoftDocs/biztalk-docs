---
title: "How to Use Variable Length Recordsets with Transaction Integrator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 173941fd-913b-43b2-aecb-82e5db356d87
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Use Variable Length Recordsets with Transaction Integrator
When data of variable length with field type of recordset is sent to the host by way of COM Transaction Integrator (COMTI), COMTI sends the final field to the host padded with NULL characters (0x00) up to the defined maximum size of the field.  
  
 When the last parameter in the type library is a recordset that refers to an OCCURS DEPENDING ON value, the null values will be passed to the mainframe unless the option Final field from host is variably sized (Return Value) is selected.  
  
 The Final field from host is variably sized (Return Value) option is located in the method's Properties on the Advanced tab.  
  
 The following trace snippet from an SNA Server Logical Unit (LU) 6.2 message trace shows the problem when the Final field from host is variably sized (Return Value) option is not selected:  
  
 PVI   ----------------------------------------------- 14:08:18.0343  
  
 PVI   0A1F0001->0102FEB1 LU 6.2  
  
 PVI                      MSGID:SWAT   MSGTYP:NTEOD  Sense1:2E00  
  
 PVI                      Sense2:0100  
  
 PVI  
  
 PVI   ---- Header  at address 01196054, 14 elements ----  
  
 PVI   0B012E00 01000400 000E0000 01007E01     \<..............~.>  
  
 PVI  
  
 PVI   ---- Element at address 01B89574, start 13, end 268 ----  
  
 PVI   2B0502FF 0003D100 0004C3E2 D4C9001A     \<+.....J...CSMI..>  
  
 PVI   11C5C3C9 C2D4C8C8 F14BE3F2 F2F1F5F8     \<.ECIBMHH1KT22158>  
  
 PVI   C4C407D0 0B100E08 00010090 0012F20D     \<DD............2.>  
  
 PVI   85020201 02000004 C3E2D4C9 12430E02     \<e.......CSMI.C..>  
  
 PVI   000006E4 00070000 0104D4E2 E3E7000B     \<...U......MSTX..>  
  
 PVI   02C3D3D3 D3C9E2C3 D3000504 14AE14B1     \<.CLLLISCL.......>  
  
 PVI   06D4C5D5 C1404040 40404040 40404040     \<.MENA@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI   40404040 40404040 40404040 40404040     \<@@@@@@@@@@@@@@@@>  
  
 PVI  
  
 PVI   ---- Element at address 01B89B28, start 13, end 268 ----  
  
 PVI   40000000 00000000 00000000 00000000     \<@...............>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   0000F0F0 F0000000 00000000 00000000     \<..000...........>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI  
  
 PVI   ---- Element at address 01B88E9C, start 13, end 268 ----  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI  
  
 PVI   ---- Element at address 01B815B4, start 13, end 268 ----  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>  
  
 PVI   00000000 00000000 00000000 00000000     \<................>