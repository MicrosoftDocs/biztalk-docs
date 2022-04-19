---
description: "Learn more about: tecwrkus"
title: "tecwrkus1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4b76119-58fa-4ac4-80af-6948a6cff40e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# tecwrkus

Tecwrkus is a 3270 user record, which includes a number of Tecwrksd LU/session information records.  
  
## Syntax  
  
```  
  
typedef struct tecwrkus {  
    USHORT   cwlen;  
    USHORT   cwtype;  
    UCHAR    cwname[21];  
    UCHAR    cwremark[26];  
    UCHAR    cwstylef[9];  
    USHORT   cwvewrtm;  
    USHORT   cwalert;  
    USHORT   cwchghan;  
    USHORT   cwmaxses;  
    USHORT   cwnumrec;  
    TECWRKSD cwsesdat[10];  
    USHORT   cwmodisf;  
    UCHAR    cwstatus;  
    UCHAR    cwpad;  
    USHORT   cwnumrmp;  
    TECWRKSD cwremap[1];  
} TECWRKUS;  
```  
  
## Members
  
*cwlen*  
Length of record.  
  
*cwtype*  
Type of record.  
  
*cwname[21]*  
User name.  
  
*cwremark[26]*  
Comment field.  
  
*cwstylef[9]*  
Initial style file name.  
  
*cwvewrtm*  
Whether user can view Response Time Monitor (RTM) information.  
  
*cwalert*  
Whether user has ALERT permission.  
  
*cwchghan*  
Whether user can change LU/pool name accessed.  
  
*cwmaxses*  
Maximum number of active sessions (1–10).  
  
*cwnumrec*  
Number of sessions for user.  
  
*cwsesdat[10]*  
Session information records.  
  
*cwmodisf*  
Permission to modify initial style.  
  
*cwstatus*  
Status byte: user or group.  
  
*cwpad*  
One byte of padding.  
  
*cwnumrmp*  
Number of LUs/pools in remap list.  
  
*cwremap[1]*  
LU/pool remap list.  
  
## Remarks

The following list of members explains the meaning of each field in the **tecwrkus** structure and indicates how the application should use each field. For more information about Host Integration Server 3270 configuration, see [Configuration Information](../core/configuration-information1.md).

*cwlen*  
The length of the 3270 user record (this is variable because it contains a variable number of LU/session records in the remap list). The application should use this value to locate the start of the next 3270 user record when searching for the correct record.  
  
*cwtype*  
Identifies this as a 3270 user record.  
  
*cwname*  
The Local Area Network (LAN) Manager user name, or other identifying name, of the 3270 user (up to 20 characters). The application uses this to search for the correct 3270 user record.  
  
*cwremark*  
An optional comment field (up to 25 characters), used in the configuration program to give more information about the user (for example, the user's full name).  
  
*cwstylef*  
The name (up to eight characters) of the default style file used by this user (a file containing the user's 3270 customization settings, used by the Host Integration Server 3270 emulation programs). This field can be used to identify the equivalent file for your 3270 emulator, if appropriate.  
  
If this field is blank, no style file is used and the 3270 emulator should revert to its default settings (unless overridden by a style file specified by the user).  
  
*cwvewrtm*  
**TRUE** if this user is permitted to view a display of RTM statistics for his or her 3270 sessions. If this field is **FALSE**, the application should not display RTM statistics and should not display a last transaction time indicator (LTTI) on the status line of display sessions. For more information about the use of Response Time Monitor (RTM), see [Diagnostics Record Format](../core/diagnostics-record-format1.md).  
  
*cwalert*  
**TRUE** if the user is permitted to send NetView user alerts. If this field is **FALSE**, the user should not be permitted to send alerts. For more information about the use of alerts, see [Diagnostics Record Format](../core/diagnostics-record-format1.md).  
  
*cwchghan*  
**TRUE** if the user is permitted to remap a 3270 session to use a different LU (in which case it can be changed to use any LU in the remap list—see **cwremap**). If this field is **FALSE**, the application should not allow the user to remap sessions.  
  
*cwmaxses*  
The maximum number of active sessions permitted to this user. If the number of sessions configured (see **cwnumrec**) is greater than this, the user must not be allowed to activate more sessions at a time than this field specifies.  
  
*cwnumrec*  
The total number of sessions configured for this user. The user record always contains 10 LU/session records (see **cwsesdat**), but only this number of the records will be used—the remainder will be filled with zeros.  
  
*cwsesdat*  
Ten LU/session records. Some of these records can be filled with zeros, indicating that they are unused (**cwnumrec** gives the number of sessions that are used). The application should list, and allow the user to use, only the sessions that have valid session records here.  
  
*cwmodisf*  
**TRUE** if the user is permitted to modify the initial 3270 customization. If this field is **FALSE**, the application should use the customization defined by **cwstylef** (if specified); the user should not be allowed to make changes to this style, or to override it by loading a different style file.  
  
*cwstatus*  
Indicates whether the user name in this record is a LAN Manager user name or group name. The least significant bit of this byte is **CERTGRUP (1)** for a group, and **zero** for a user. Other bits are not used.  
  
*cwpad*  
Pad byte—not used by the application.  
  
*cwnumrmp*  
The number of LU/session records in the remap list (see **cwremap**).  
  
*cwremap*  
The list of LU/session records, which indicates the LUs to which the user can remap sessions (if any). If the user is not permitted to remap sessions (see **cwchghan**), this list is not used and should not be checked by the application.