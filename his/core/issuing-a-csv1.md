---
title: "Issuing a CSV1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 522f14ee-ebea-4d1b-9b84-f7cb01df10a2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Issuing a CSV
The procedure for issuing a CSV is shown in the following sample code that uses [CONVERT](./convert2.md).  
  
### To issue a CSV  
  
1.  Create a structure variable from the verb control block (VCB) structure that applies to the verb to be issued.  
  
    ```  
    #include <wincsv.h>  
        .  
        .  
    struct convert  conv_block;  
  
    ```  
  
     The VCB structures are declared in the WINCSV.H file; one of these structures is named **CONVERT**.  
  
2.  Clear (set to zero) the variables within the structure.  
  
    ```  
    memset( conv_block, '\0', sizeof( conv_block ) );  
  
    ```  
  
     This procedure is not required. However, it helps in debugging and reading the contents of memory. It also eliminates the possibility that future versions of a verb are sensitive to fields that are ignored in the current version.  
  
3.  Assign values to the required VCB variables.  
  
    ```  
    conv_block.opcode = SV_CONVERT;  
    conv_block.direction = SV_ASCII_TO_EBCDIC;  
    conv_block.char_set = SV_AE;  
    conv_block.len = sizeof(tpstart_name);  
    conv_block.source = (LPBYTE) tpstart_name;  
    conv_block.target = (LPBYTE) tpstart.tp_name;  
  
    ```  
  
     The values SV_CONVERT, SV_ASCII_TO_EBCDIC, and SV_AE are symbolic constants representing integers. These constants are defined in the WINCSV.H file.  
  
     The character array TPSTART_NAME contains an ASCII string to be converted to EBCDIC and placed in the character array TPSTART.TP_NAME.  
  
4.  Invoke the verb. The only parameter is a pointer to the address of the structure containing the VCB for the verb.  
  
    ```  
    ACSSVC((LONG) &conv_block);  
  
    ```  
  
     You can also use the following statement:  
  
    ```  
    ACSSVC_C((LONG) &conv_block);  
  
    ```  
  
5.  Use the values returned by the verb.  
  
    ```  
    if( conv_block.primary_rc == SV_OK ) {  
    /* other statements */  
        .  
        .  
        .  
    ```