---
title: "DISPLAY2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ac37c64-c95a-41f7-a47b-3579ad2ff869
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# DISPLAY
The **DISPLAY** verb returns configuration information and current operating values for the SNA node.  
  
 It is recommended that you use the [GetAppcConfig](../core/getappcconfig1.md) Windows extension function to obtain system configuration information relating to APPC LUs. Users of 5250 emulators, in particular, should use the **GetAPPCConfig** Windows extension.  
  
> [!NOTE]
>  Because of the nature of client/server architecture, the implementation of the **DISPLAY** verb on Host Integration Server contains important differences from the IBM Extended Services for OS/2 version 1.0 (IBM ES for OS/2 version 1.0) on which it was based.  
  
> [!NOTE]
>  For applications that use the APPC **DISPLAY** verb in IBM ES for OS/2 version 1.0 compatibility mode and that do not use the Host Integration Server extensions for enumerating all active servers and connections, Host Integration Server will randomly choose a default **DISPLAY** connection, unless a specific default **DISPLAY** connection has been configured in SNA Manager. This connection is used as the basis for all **DISPLAY** requests. For information about specifying the default **DISPLAY** connection, see Host Integration Server Help.  
  
 The following structure describes the verb control block used by the **DISPLAY** verb.  
  
## Syntax  
  
```  
  
struct display {  
    unsigned short  opcode;  
    unsigned char   reserv2[2];  
    unsigned short  primary_rc;  
    unsigned long   secondary_rc;  
    unsigned long   init_sect_len;  
    unsigned long   buffer_len;  
    unsigned char FAR * buffer_ptr;  
    unsigned long  num_sections;  
    unsigned long  display_len;  
    unsigned long  area_needed;  
    unsigned char  sna_global_info;  
    unsigned char  lu62_info;  
    unsigned char  am_info;  
    unsigned char  tp_info;  
    unsigned char  sess_info;  
    unsigned char  link_info;  
    unsigned char  lu_0_3_info;  
    unsigned char  gw_info;  
    unsigned char  x25_physical_link_info;  
    unsigned char  sys_def_info;  
    unsigned char  adapter_info;  
    unsigned char  lu_def_info;  
    unsigned char  plu_def_info;  
    unsigned char  mode_def_info;  
    unsigned char  link_def_info;  
    unsigned char  ms_info;  
    struct sna_global_info_sect FAR * sna_global_info_ptr;  
    struct lu62_info_sect FAR * lu62_info_ptr;  
    struct am_info_sect FAR * am_info_ptr;  
    struct tp_info_sect FAR * tp_info_ptr;  
    struct sess_info_sect FAR * sess_info_ptr;  
    struct link_info_sect FAR * link_info_ptr;  
    struct lu_0_3_info_sect FAR * lu_0_3_info_ptr;  
    struct gw_info_sect FAR * gw_info_ptr;  
    struct x25_physical_link_info_sect FAR * x25_physical_link_info_ptr;  
    struct sys_def_info_sect FAR * sys_def_info_ptr;  
    struct adapter_info_sect FAR * adapter_info_ptr;  
    struct lu_def_info_sect FAR * lu_def_info_ptr;  
    struct plu_def_info_sect FAR * plu_def_info_ptr;  
    struct mode_def_info_sect FAR * mode_def_info_ptr;  
    struct link_def_info_sect FAR * link_def_info_ptr;  
    struct ms_info_sect FAR * ms_info_ptr;  
} DISPLAY;   
```  
  
## Members  
 opcode  
 Supplied parameter. Specifies the verb operation code, AP_DISPLAY.  
  
 reserv2  
 A reserved field, this value must be set to NULL.  
  
 primary_rc  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 secondary_rc  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 init_sect_len  
 Supplied parameter. Specifies the number of bytes in the initial section of the VCB, up to the beginning of information pointers. This parameter and the **num_sections** parameter must be set to specific values depending on the format being requested. See the notes below for details.  
  
 buffer_len  
 Supplied parameter. Specifies the length (0 to 65535 bytes) of the passed display data buffer.  
  
 buffer_ptr  
 Supplied parameter. Provides the address of the display data buffer that will contain the requested information.  
  
 num_sections  
 Supplied parameter. Specifies the maximum number of information sections that can be returned by the verb. This parameter and the **init_sect_len** parameter must be set to specific values depending on the format being requested. See the notes below for details.  
  
 display_len  
 Returned parameter. Provides the total number of bytes used that are returned into the display data buffer.  
  
 area_needed  
 Returned parameter. Provides the total number of bytes needed for all of the displayed data.  
  
 sna_global_info  
 Supplied parameter. Specifies if global information is requested. Allowed values are AP_YES and AP_NO.  
  
 lu62_info  
 Supplied parameter. Specifies if information on all active LUs, their partners, and their modes is requested. Allowed values are AP_YES and AP_NO.  
  
 am_info  
 Supplied parameter. Specifies if Attach Manager information on the defined TP is requested. Allowed values are AP_YES and AP_NO.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server and this parameter must be set to AP_NO.  
  
 tp_info  
 Supplied parameter. Specifies if information on the active TPs and any active conversations is requested. Allowed values are AP_YES and AP_NO.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server and this parameter must be set to AP_NO.  
  
 sess_info  
 Supplied parameter. Specifies if information on sessions is requested. Allowed values are AP_YES and AP_NO.  
  
 link_info  
 Supplied parameter. Specifies if information on the active SNA logical lines is requested. Allowed values are AP_YES and AP_NO.  
  
 lu_0_3_info  
 Supplied parameter. Specifies if information on logical units type 0, 1, 2, and 3 is requested. Allowed values are AP_YES and AP_NO.  
  
 gw_info  
 Supplied parameter. Specifies if information on the SNA gateway is requested. Allowed values are AP_YES and AP_NO.  
  
 x25_physical_link_info  
 Supplied parameter. Specifies if X.25 information is required. Allowed values are AP_YES and AP_NO.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server and this parameter must be set to AP_NO.  
  
 sys_def_info  
 Supplied parameter. Specifies if information about the default LU, node names, and default parameters for inbound and outbound implicit partners is requested. Allowed values are AP_YES and AP_NO.  
  
 adapter_info  
 Supplied parameter. Specifies if information about the configured communications adapters is requested. Allowed values are AP_YES and AP_NO. This parameter must be set to AP_NO when NS/2 format is requested.  
  
 lu_def_info  
 Supplied parameter. Specifies if information about the defined LUs is requested. Allowed values are AP_YES and AP_NO.  
  
 plu_def_info  
 Supplied parameter. Specifies if information about the defined partner LUs is requested. Allowed values are AP_YES and AP_NO.  
  
 mode_def_info  
 Supplied parameter. Specifies if information about the defined nodes is requested. Allowed values are AP_YES and AP_NO.  
  
 link_def_info  
 Supplied parameter. Specifies if information about the defined logical links is requested. Allowed values are AP_YES and AP_NO.  
  
 ms_info  
 Supplied parameter. Specifies if information about management services is requested. Allowed values are AP_YES and AP_NO. This parameter must be set to AP_NO when NS/2 format is requested.  
  
 sna_global_info_ptr  
 Returned parameter. Indicates the address of the beginning of SNA global information in the data buffer.  
  
 lu62_info_ptr  
 Returned parameter. Indicates the address of the beginning of LU 6.2 information in the data buffer.  
  
 am_info_ptr  
 Returned parameter. Indicates the address of the beginning of the Attach Manager information in the data buffer.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server.  
  
 tp_info_ptr  
 Returned parameter. Indicates the address of the beginning of TP information in the data buffer.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server.  
  
 sess_info_ptr  
 Returned parameter. Indicates the address of the beginning of session information in the data buffer.  
  
 link_info_ptr  
 Returned parameter. Indicates the address of the beginning of link information in the data buffer.  
  
 lu_0_3_info_ptr  
 Returned parameter. Indicates the address of the beginning of LU information in the data buffer.  
  
 gw_info_ptr  
 Returned parameter. Indicates the address of the beginning of gateway information in the data buffer.  
  
 x25_physical_link_info_ptr  
 Returned parameter. Indicates the address of the beginning of X.25 information in the data buffer.  
  
> [!NOTE]
>  This option is not supported by Host Integration Server.  
  
 sys_def_info_ptr  
 Returned parameter. Indicates the address of the beginning of system default information in the data buffer.  
  
 adapter_info_ptr  
 Returned parameter. Indicates the address of the beginning of adapter information in the data buffer.  
  
 lu_def_info_ptr  
 Returned parameter. Indicates the address of the beginning of local LU definition information in the data buffer.  
  
 plu_def_info_ptr  
 Returned parameter. Indicates the address of the beginning of partner LU definition information in the data buffer.  
  
 mode_def_info_ptr  
 Returned parameter. Indicates the address of the beginning of mode definition information in the data buffer.  
  
 link_def_info_ptr  
 Returned parameter. Indicates the address of the beginning of link definition information in the data buffer.  
  
 ms_info_ptr  
 Returned parameter. Indicates the address of the beginning of management services information in the data buffer.  
  
## Return Codes  
 AP_OK  
 Primary return code; the verb executed successfully.  
  
 AP_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 AP_DISPLAY_INVALID_CONSTANT  
 Secondary return code; the value supplied for NUM_SECTIONS or INIT_SEC_LEN is invalid.  
  
 AP_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 AP_DISPLAY_INFO_EXCEEDS_LEN  
 Secondary return code; the returned **DISPLAY** information did not fit in the buffer.  
  
 AP_INVALID_DATA_SEGMENT  
 Secondary return code; the segment containing the data buffer is too small for the specified data length.  
  
 AP_COMM_SUBSYSTEM_ABENDED  
 Primary return code; indicates one of the following conditions:  
  
 The node used by this conversation has encountered an ABEND.  
  
 The connection between the TP and the node type 2.1 has been broken (a LAN error).  
  
 The SnaBase at the TPs computer has encountered an ABEND.  
  
 AP_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 AP_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 AP_STACK_TOO_SMALL  
 Primary return code; the stack size of the application is too small to execute the verb. Increase the stack size of your application.  
  
 AP_UNEXPECTED_DOS_ERROR  
 Primary return code; the operating system has returned an error to APPC while processing an APPC call from the local TP. The operating system return code is returned through the **secondary_rc**. It appears in Intel byte-swapped order. If the problem persists, consult the system administrator.  
  
## Remarks  
 **DISPLAY** identifies an LU by alias alone. If the same local LU alias is used multiple times in a domain (for backup or other purposes) and that LU alias is specified through **DISPLAY**, the verb can flow to a different LU than the one intended.  
  
 For the **DISPLAY** verb to return successfully, a specific connection must be defined in the SNA Manager program **Display Verb** dialog box. IBM originally defined the **DISPLAY** verb with the IBM OS/2 Extended Edition product which assumed a single connection. However, because Host Integration Server supports multiple connections, the specific connection associated with the **DISPLAY** verb must be configured.  
  
 The **DISPLAY** verb requires a user-supplied buffer for the return of system information. If the buffer is not large enough, APPC returns the AP_DISPLAY_INFO_EXCEEDS_LEN return code, along with the size actually needed at the time of the request (in the **area_needed** parameter). One possible strategy for the use of this verb follows:  
  
- If the **buffer_len** value is less than the **area_needed** value returned by APPC, and the required length is less than 64 kilobytes (KB), then increase the size of the display buffer to equal or greater than the **area_needed** value.  
  
- If the **area_needed** value is greater than 64KB, you can choose to request each information section individually. Or, you can take the following steps:  
  
  1.  Process the information sections with complete information, whose total number displayed equals the total actual number.  
  
  2.  Choose a subset of the information sections you requested that contains incomplete information, and reissue the verb requesting those information sections.  
  
  3.  Repeat steps a and b as needed.  
  
  > [!NOTE]
  >  If an individual information section is greater than 64 KB, then you cannot get all of the requested information from APPC.  
  
  The **DISPLAY** verb should not be executed from different threads of the same process, since it is not thread-safe.  
  
  The **DISPLAY** verb returns AP_DISPLAY_INVALID_CONSTANT if the following values are not set for the supplied parameters for **init_sect_len** and **num_sections**:  
  
||NS/2 format|IBM EE format|NS/2 format (Windows only)|IBM EE format (Windows only)|  
|------|------------------|-------------------|-----------------------------------|------------------------------------|  
|**init_sect_len**|50|44|52|48|  
|**num_sections**|16|9|16|9|  
  
 The AP_DISPLAY_INVALID_CONSTANT is also returned when the following parameters are not set properly:  
  
-   **reserv2** must be set to NULL.  
  
-   **am_info** must be set to AP_NO.  
  
-   **tp_info** must be set to AP_NO.  
  
-   **adapter_info** must be set to AP_NO if NS/2 format is requested.  
  
-   **ms_info** must be set to AP_NO if NS/2 format is requested.  
  
## See Also  
 [Host Integration Server Extensions](../core/host-integration-server-extensions1.md)   
 [Differences by Information Type](../core/differences-by-information-type1.md)