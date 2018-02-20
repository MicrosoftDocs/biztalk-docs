---
title: "Issuing an APPC Verb1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3819c4d-570c-4a2a-a9b5-422b2f6bbe41
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Issuing an APPC Verb
The following procedure is required to issue a blocking APPC verb. In the sample code, the verb issued is **MC_SEND_DATA**.  
  
### To issue a blocking APPC verb  
  
1.  Create a structure variable from the verb control block (VCB) structure that applies to the APPC verb to be issued.  
  
    ```  
    #include <winappc.h>  
        .  
        .  
    struct mc_send_data  mcsend;  
    The VCB structures are declared in WINAPPC.H; one of these structures is:  
    mc_send_data  
    ```  
  
2.  Clear (set to zero) the variables within the VCB structure.  
  
    ```  
    memset( mcsend, '\0', sizeof( mcsend ) );  
    ```  
  
3.  Assign values to the VCB variables that supply information to APPC.  
  
    ```  
    mcsend.opcode = AP_M_SEND_DATA;  
    mcsend.opext = AP_MAPPED_CONVERSATION;  
    memcpy( mcsend.tp_id, tp_id, sizeof( tp_id ) );  
    mcsend.conv_id = conv_id;  
    mcsend.dlen = datalen;  
    mcsend.dptr = sharebufptr;  
    ```  
  
     The values AP_MAPPED_CONVERSATION and AP_M_SEND_DATA are symbolic constants representing integers. These constants are defined in WINAPPC.H.  
  
4.  Invoke the **APPC** function. The only parameter is a pointer to the address of the structure containing the VCB for the desired verb.  
  
    ```  
    APPC ( ( long ) (void FAR * ) &mcsend );  
    ```  
  
     Use [WinAsyncAPPC](./winasyncappc1.md) if you are running the application under Windows version 3.*x*.  
  
     To call **WinAsyncAPPC**:  
  
    ```  
    HANDLE WINAPI WinAsyncAPPC (hWnd, 1pVCB)  
    ```  
  
     When the asynchronous operation is complete, the application's window *hWnd* receives the message returned by **RegisterWindowMessage** with "WinAsyncAPPC" as the input string.  
  
5.  Use the variables that were returned by APPC.  
  
    ```  
    if( mcsend.primary_rc != AP_OK )   
    /* Do error routine */  
        .  
        .  
        .  
    ```