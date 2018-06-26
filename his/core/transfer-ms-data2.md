---
title: "TRANSFER_MS_DATA2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4eb8badf-799f-45e2-8e44-7fdcbecda742
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TRANSFER_MS_DATA
The **TRANSFER_MS_DATA** verb builds an SNA request unit containing Network Management Vector Transport (NMVT) data. The verb can send the NMVT data to NetView for centralized problem diagnosis and resolution. The data is logged in the local audit file.  
  
 The following structure describes the verb control block (VCB) used by the **TRANSFER_MS_DATA** verb.  
  
## Syntax  
  
```  
  
struct transfer_ms_data {  
    unsigned short       opcode;  
    unsigned char        data_type;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned char        options;  
    unsigned char        reserv3;  
    unsigned char        origntr_id[8];  
    unsigned short       dlen;  
    unsigned char FAR *  dptr;  
};  
```  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_TRANSFER_MS_DATA.  
  
 *data_type*  
 Supplied parameter. Specifies the type of data provided by this verb:  
  
- Use SV_NMVT to generate an NMVT (including the NS header, the major network management vector, and subvectors).  
  
- Use SV_ALERT_SUBVECTORS to generate an RU containing data for an alert in the appropriate format, without the NS header or major NMVT vector.  
  
- Use SV_PDSTATS_SUBVECTORS to generate an RU containing data for problem determination statistics in the appropriate format, without the NS header or major NMVT vector.  
  
- Use SV_USER_DEFINED to generate user-defined data; this data is recorded in the error log but cannot be sent on the systems services control point-physical unit (SSCP-PU) session on the connection configured for diagnostics.  
  
  *reserv2*  
  A reserved field.  
  
  *primary_rc*  
  Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
  *secondary_rc*  
  Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
  *options*  
  Supplied parameter. Specifies the desired options by turning individual bits on or off. (Bits 1, 2, and 3 are ignored if **data_type** is set to SV_USER_DEFINED.) See the Remarks section.  
  
  reserv3  
  A reserved field.  
  
  *origntr_id*  
  Supplied parameter. Specifies the name of the component issuing **TRANSFER_MS_DATA**. This parameter is optional. Set it to 0x00 if you want the system to ignore it.  
  
  *dlen*  
  Supplied parameter. Specifies the length of data to be supplied to this verb. The total length of the data (user-supplied data and any added headers or subvectors) must fit into one RU. The maximum RU length is 512 bytes.  
  
  *dptr*  
  Supplied parameter. Specifies the address of the data to be sent.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_DATA_EXCEEDS_RU_SIZE  
  
 Secondary return code; the data to be sent was too long. The length of the user-supplied data plus headers and added subvectors must fit in a single RU that is not more than 512 bytes long.  
  
 SV_INVALID_DATA_SEGMENT  
  
 Secondary return code; the buffer pointed to by **dptr** was not a readable segment or extended beyond the segment boundary.  
  
 SV_INVALID_DATA_TYPE  
  
 Secondary return code; the **data_type** parameter contained an invalid value.  
  
 SV_STATE_CHECK  
 Primary return code; the verb did not execute because it was issued in an invalid state.  
  
 SV_SSCP_PU_SESSION_NOT_ACTIVE  
  
 Secondary return code; the NMVT was not sent; either the SSCP-PU session was not active, the node configured to receive diagnostic information was not active, or no network management connection was configured.  
  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 SV_INVALID_VERB  
 Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
 SV_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 SV_UNEXPECTED_DOS_ERROR  
 Primary return code; one of the following conditions occurred:  
  
- The Microsoft Windows operating system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
- A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
- A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
  SV_CANCELLED  
  Primary return code; this code is returned for an asynchronous verb when it has been shut down by a [WinCSVCleanup](../core/wincsvcleanup1.md) call.  
  
  SV_SERVER_RESOURCE_NOT_FOUND  
  Primary return code; no communication server was found that could provide the requested function.  
  
  SV_SERVER_RESOURCES_LOST  
  Primary return code; the communications server that was providing the function was lost due to a connection failure.  
  
  SV_SERVER_CONN_FAILURE  
  
  Secondary return code; the connection to the server was lost due to physical path problems; for example, the server may have been powered off.  
  
  SV_THREAD_BLOCKING  
  Primary return code; this verb exceeds the maximum number of simultaneous synchronous verbs allowed.  
  
## Remarks  
 To specify options, turn bits on or off as follows:  
  
|Bit|Description|  
|---------|-----------------|  
|0|TIME_STAMP_SUBVECTOR. Adds date/time subvector to data. Allowed values include SV_ADD and SV_NO_ADD.|  
|1|PRODUCT_SET_ID_SUBVECTOR. Adds Product_Set_ID subvector to data. This allows network management services to identify the sender of an alert. Allowed values include SV_ADD and SV_NO_ADD.|  
|2|SSCP_PU_SESSION. Sends the data on the SSCP-PU session on the connection configured for diagnostics if the session is active. (The data is added to the error log regardless of whether it is sent on the session or whether SV_STATE_CHECK or SV_COMM_SUBSYSTEM_NOT_LOADED is returned.) Allowed values include SV_SEND and SV_NO_SEND.|  
|3|LOCAL_LOGGING. Logs local alerts that are retrieved from the error log and forwarded to the host. This option is valid only when **data_type** SV_NMVT or **data_type** SV_ALERT_SUBVECTORS with option SV_SEND is specified. Allowed values include SV_LOG and SV_NO_LOG.|  
|4 through 7|Reserved|