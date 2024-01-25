---
description: "Learn more about: Open(SSCP) Request"
title: "Open(SSCP) Request2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Open(SSCP) Request
The **Open(SSCP) Request** message flows from the application to the node. It is used with a system services control point (SSCP) connection.  
  
## Syntax  
  
```  
struct Open(SSCP) Request {  
    PTRBFHDR  nxtqptr;  
    PTRBFELT  hdrept;  
    CHAR      numelts;  
    CHAR      msgtype;  
    CHAR      srcl;  
    CHAR      srcp;  
    INTEGER   srci;  
    CHAR      destl;  
    CHAR      destp;  
    INTEGER   desti;  
    CHAR      ophdr.openqual;  
    CHAR      ophdr.opentype;  
    CHAR      ophdr.appltype;  
    CHAR      ophdr.opluno;  
    INTEGER   ophdr.opresid;  
    INTEGER   ophdr.icreditr;  
    INTEGER   ophdr.icredits;  
    CHAR      ophdr.opninfo1;  
    CHAR      ophdr.opnpad1;  
};   
struct Open(SSCP) Request {  
    PTRBFELT   hdreptr->elteptr;  
    INTEGER    hdreptr->startd;  
    INTEGER    hdreptr->endd;  
    CHAR       hdreptr->trpad;  
    CHAR[268]  hdreptr->dataru;  
};  
struct Open(SSCP) Request {  
    PTRBFELT  hdreptr->elteptr->elteptr;  
    INTEGER   hdreptr->elteptr->startd;  
    INTEGER   hdreptr->elteptr->endd;  
    CHAR      hdreptr->elteptr->trpad;  
    CHAR[268] hdreptr->elteptr->dataru;  
};  
```  
  
## Members  
 *nxtqptr*  
 Pointer to next buffer header.  
  
 *hdrept*  
 Pointer to first buffer element.  
  
 *numelts*  
 Number of buffer elements (0x02).  
  
 *msgtype*  
 Message type OPENMSG (0x01).  
  
 *srcl*  
 Source locality.  
  
 *srcp*  
 Source partner. (For more information, see Remarks.)  
  
 *srci*  
 Source index.  
  
 *destl*  
 Destination locality.  
  
 *destp*  
 Destination partner.  
  
 *desti*  
 Destination index.  
  
 *ophdr.openqual*  
 Open qualifier REQU  (0x01).  
  
 *ophdr.opentype*  
 Open type SSCPSEC  (0x01).  
  
 *ophdr.appltype*  
 Application program interface type.  
  
 Function management interface (FMI) without chunking    (0x02).  
  
 FMI with chunking        (0x82). (For more information, see Remarks.)  
  
 *ophdr.opluno*  
 Logical Unit number. (For more information, see Remarks.)  
  
 *ophdr.opresid*  
 Resource identifier.  
  
 *ophdr.icreditr*  
 Reserved.  
  
 *ophdr.icredits*  
 Reserved.  
  
 *ophdr.opninfo1*  
 Reserved.  
  
 *ophdr.opnpad1*  
 Open force type. (For more information, see Remarks.)  
  
 OPEN_TEST       (0x00)  
  
 OPEN_FORCE    (0x01)  
  
 **Element 1**  
  
 *hdreptr–>elteptr*  
 Pointer to next buffer element.  
  
 *hdreptr–>startd*  
 Start of data in this buffer element (1).  
  
 *hdreptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>trpad*  
 Reserved (1 byte).  
  
 *hdreptr–>dataru*  
 Data request/response unit (RU), as follows:  
  
 dataru[0–9]  
  
 Source name. Should be filled with blanks.  
  
 dataru[10–19]  
  
 Destination name. Set to the logical unit (LU) with which you want to communicate.  
  
 dataru[20]  
  
 Sense 4003 flag.  
  
 dataru[21]  
  
 Sense 4004 flag.  
  
 dataru[22]  
  
 Sense 4006 flag.  
  
 dataru[23]  
  
 Sense 4007 flag.  
  
 dataru[24]  
  
 Sense 4009 flag.  
  
 dataru[25]  
  
 Sense 400A flag.  
  
 dataru[26]  
  
 Sense 400B flag.  
  
 dataru[27]  
  
 Sense 400C flag.  
  
 dataru[28]  
  
 Sense 400D flag.  
  
 dataru[29]  
  
 Sense 400F flag.  
  
 dataru[30]  
  
 Sense 4011 flag.  
  
 dataru[31]  
  
 Sense 4012 flag.  
  
 dataru[32]  
  
 Sense 4014 flag.  
  
 dataru[33]  
  
 High priority indicator.  
  
 HIGH    (0x01)  
  
 LOW    (0x02)  
  
 dataru[34]  
  
 Logical unit application (LUA) supported indicator.  
  
 Supported          (0x01)  
  
 Not supported    (0x00)  
  
 dataru[35–36]  
  
 Chunk size obtained from Dynamic Access Module (DMOD). (For more information, see Remarks.)  
  
 dataru[37]  
  
 Segment delivery option.  
  
 Do not deliver request/response unit (RU) segments    (0x00)  
  
 Deliver RU segments              (0x01)  
  
 dataru[38]  
  
 High-level language application programming interface (HLLAPI) session identifier. (For more information, see Remarks.)  
  
 **Element 2**  
  
 *hdreptr–>elteptr–>elteptr*  
 Pointer to next buffer element (NIL).  
  
 *hdreptr–>elteptr–>startd*  
 Start of data in this buffer element (1).  
  
 *hdreptr–>elteptr–>endd*  
 End of data in this buffer element.  
  
 *hdreptr–>elteptr–>trpad*  
 Reserved.  
  
 *hdreptr–>elteptr–>dataru*  
 Data RU, as follows:  
  
 dataru[0]  
  
 ASCII string identifying the 3270 emulator. (For more information, see Remarks.)  
  
## Remarks  
  
-   The **Open(SSCP) Request** message consists of a buffer header and two buffer elements.  
  
-   The source L value, the destination Locality Partner Index (LPI) values, and the source name are reserved.  
  
-   For a 3270 emulator, the source P value must be set to S3PROD (0x12), which identifies the application as a 3270 emulator. The destination name should be set to the LU name or pool name taken from the 3270 user record (right-filled with ASCII spaces if fewer than 10 characters).  
  
-   An LUA application uses the source P value LUAPROD (0x1D). This is independent of the value of the LUA supported indicator, which selects the LUA variant of the FMI.  
  
-   The SNS4003 to SNS4014 fields, together with the high priority indicator, are referred to in the text as the SSCP connection information control block (CICB). (For more information, see [Opening the SSCP Connection](./opening-the-sscp-connection1.md).) A value of 0x00 indicates that the data flow control (DFC) receive check corresponding to the sense code is not supported for this LU. A value of 0x01 indicates that it is supported. Note that the corresponding send checks are always performed regardless of these values.  
  
-   The LU number is only used internally in the local node on the **Open(SSCP) Request**. It is generated from the destination name in the first element.  
  
-   The open force type field is used when locating resources across more than one server and for automatic activation of connections when the application wishes to use an LU for which the connection is inactive. The application does not need to set this flag. It is used by the DL-BASE. For details, see [Opening the SSCP Connection](./opening-the-sscp-connection1.md).  
  
-   The application program interface type field defines whether RU chunking is used from the local node to the application. This may be necessary if large RUs are being used. For more information about FMI chunking, see [Pacing and Chunking](./pacing-and-chunking1.md).  
  
-   The chunk size field (at **dataru[35]**) is an integer value.  
  
-   The segment delivery option specifies whether the local node should deliver segments of RUs to the application as soon as they are received or should assemble whole RUs before delivering them to the application. Segment delivery allows the application to update the user's screen as soon as data is received, known as window shading, which can result in a faster perceived response. For more information, see [Segment Delivery](./segment-delivery1.md). This option is required only when chunking is being used. It is included on this message so that the local node can calculate the initial chunk credit values on the corresponding primary logical unit (PLU) connection. The option must still be set on the **Open(PLU) Response**. The setting specified on that message will override the one specified here if there is a conflict. If this happens, the initial credit values may not be suitable.  
  
-   The LUA supported indicator specifies whether the application uses the LUA variant of the FMI.  
  
-   If the element is shorter than (s+34) bytes, Microsoft® Host Integration Server assumes no LUA and no chunking. This ensures backward compatibility with previous versions of the local node software in which these options were not available.  
  
-   The HLLAPI session identifier is a single ASCII character that identifies the 3270 display session to which the **Open(SSCP)** applies. HLLAPI uses this to identify a particular 3270 presentation space to which an HLLAPI function refers. It is also referred to by 3270 as the session's short name, or by HLLAPI as the presentation space identifier (PS identifier). If the 3270 emulator does not support session identifiers, this field should be set to zero.  
  
-   The second element contains an ASCII string that you can use to identify the type of 3270 emulator. This string will be logged in the audit log file by the client's DL-BASE and can also be seen in traces. The **startd** and **endd** fields must be set up to define the limits of this string.
