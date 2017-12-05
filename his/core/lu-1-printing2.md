---
title: "LU 1 Printing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1747cc9-9ba2-4eb2-a0e6-24f6d467fcb9
caps.latest.revision: 3
---
# LU 1 Printing
LU 1 printing allows the host to specify formatting for a print job. This is accomplished through the use of SNA Character String (SCS) control codes. The SCS codes encompass the 3270 format orders (FF, CR, and NL), as well as providing additional control codes to format the print output. Through the SCS codes, the host application can set the margins, characters per line, and lines per inch. In addition to the format of the print job, SCS code allows the host application to send a transparent section. By using an SCS code, the host can mark a section of data as transparent. This will cause the print emulator (the Host Print service in this case) to not scan this section for SCS control codes but to pass it to the print output untouched. Transparent sections are most commonly used to embed printer control codes, such as the HP PCL, in the print job. Unlike LU 3 printing, there is no write command code or WCC. The first byte of the RU is either an SCS code or data.  
  
## Data Stream Flags  
 The BIND sent by the host for a LU 1 session indicates what SCS control codes are valid for this session. These Data Stream Flags are set in byte 18 of the BIND.  
  
### Data Stream Flags  
  
|Bit|Value|Description|  
|---------|-----------|-----------------|  
|**0**||**Base SCS code support**|  
||0|**Base support** (NL & FF only)|  
||1|**Full Base** includes Base plus the following:|  
|||BS (back space)|  
|||CR (carriage return)|  
|||LF (line feed)|  
|||ENP (enable presentation)|  
|||INP (inhibit presentation)|  
|||HT (horizontal tab)|  
|||VT (vertical tab)|  
|**1**||**Set Horizontal Format** (SHF)|  
||0|not supported|  
||1|supported|  
|**2**||**Set Vertical Format** (SVF)|  
||0|not supported|  
||1|supported|  
|**3**||**Vertical Channel Select** (VCS)|  
||0|not supported|  
||1|supported|  
|**4**||**Set Line Density** (SLD)|  
||0|not supported|  
||1|supported|  
|**5**||**Reserved**|  
|**6**||**Bell** (BEL)|  
||0|not supported|  
||1|supported|  
|**7**||**Transparent** (TRN) &  **Interchange Record Separator** (IRS)|  
||0|not supported|  
||1|supported|  
  
## SCS Codes  
 The SCS control codes are fully documented in the IBM Host Print Guide (document number SC31-7145). All of the SCS control codes fall within the range of '0x00'–'0x3F.' These codes range from single byte codes, such as Subscript '0x38', to multiple byte codes followed by several parameters, such as Set Horizontal Format '0x2BC1...'  
  
 The following are some of the more common SCS control codes used.  
  
> [!NOTE]
>  [L]=length and **(Abv)** represents one-byte parameters in the SCS control code.  
  
 **Set Horizontal Format (SHF) — '0x2BC1[L](MPP\)(LM)(RM)(T1)(. . .)(Tn)'**  
  
 [L] — Length of the parameters, including the length byte  
  
 MPP — Maximum Presentation Position; defines the characters per line  
  
 LM — Left Margin; column value for the left most print position  
  
 RM — Right Margin; column value for the right most print position  
  
 T1 — Horizontal tab stop; column value for a tab stop  
  
 Tn — Additional tab stops, which can be added in any order  
  
 **Example**  
  
 2BC1068401840542  
  
 2BC1 — SHF  
  
 06 — length of the parameters is 6 bytes including the length byte  
  
 84 — MPP is set to 132 characters per line  
  
 01 — LM is set to column 1  
  
 84 — RM is set to column 132  
  
 05 — T1 is set to column 5  
  
 42 — T2 is set to column 66  
  
 **Set Vertical Format (SVF) — '0x2BC2[L](MPL\)(TM)(BM)(T1)(. . .)(Tn)'**  
  
 [L] — Length of the parameters, including the length byte  
  
 MPL — Maximum Presentation Line; defines the lines per page  
  
 TM — Top Margin; line number of top most print position  
  
 BM — Bottom Margin; line number of the bottom most print position  
  
 T1 — Vertical Tab Stop; line number for a tab stop  
  
 Tn — Additional Tab Stops, which can be added in any order  
  
 **Example**  
  
 2BC20642053D0A21  
  
 2BC2 — SVF  
  
 06 — length is 6 bytes  
  
 42 — MPL is set to 66 lines per page  
  
 05 — TM is set to line 5  
  
 3D — BM is set to line 61  
  
 0A — T1 is set to line 10  
  
 21 — T2 is set to line 33  
  
 **Set Line Density (SLD) — '0x2BC6[L](Point\)'**  
  
 [L] — length, including length byte. Value of '0x01' denotes default.  
  
 Point — Distance to be moved vertically for a single line. The number is indicated in typographic points (one point is equal to 1/72 inch). Setting a value of '0x0C' will result in 6 lines per inch, a value of '0x09' will result in 8 lines per inch. Value of '0x00' denotes default a value of 6 lines per inch.  
  
 **Example**  
  
 2BC6020C  
  
 2BC6 — SLD  
  
 02 — length is 2  
  
 0C — 12 points or 6 lines per inch  
  
 **Set Print Density (SPD) '0x2BD2[L]29(CharDensity)(Resv)'**  
  
 [L] — length, including length byte. Value of 0x02 denotes default characters per inch (cpi) of 10  
  
 CharDensity — value indicating the numbers of cpi  
  
 Resv — Reserved (not used)  
  
 **Example**  
  
 2BD204290A00  
  
 2BD2 — SPD  
  
 04 — length is 4 bytes  
  
 29 — type  
  
 0A — 10 cpi  
  
 00 — reserved  
  
 **Transparent (TRN) — '0x35[L](P1\)(. . .)(Pn)'**  
  
 This SCS control code indicates a section of data that is not scanned for SCS codes, but passed to the print output untouched. The extent of the section of data is denoted by the length byte.  
  
 **Example**  
  
 35051B28313055  
  
 35 — TRN  
  
 05 — length of transparent section, not including the length byte  
  
 1B28313055 — transparent section, HP PCL code for PC-8 symbol set 'Esc(10U'  
  
> [!NOTE]
>  In this example, the transparent section is in ASCII. This would require that the "Transparent is ASCII" box be selected in the Print Services printer session properties in the SNA Manager.  
  
## Sample Host Data  
 Following is sample data from a host along with an explanation of the data and resulting printout.  
  
```  
35021B45 2BC10684 01840542 2BC20642   
04420A21 C1C2C3C4 15404040 E6E7E8E9  
  
```  
  
### 3270 LU 1 Sample Data  
  
|Data|Interpretation|  
|----------|--------------------|  
|35021B45|Transparent section, send 'Esc E', a Reset in HP PCL, to printer|  
|2BC1068401840542|SHF, 132 characters per line, LM 1, RM 132|  
|2BC2064204420A21|SVF, 66 lines per page, TM 4, BM 66|  
|C1C2C3C4|EBCDIC hex values for ABCD|  
|15|New line|  
|404040|EBCDIC hex values for three spaces|  
|E6E7E8E9|EBCDIC hex values for WXYZ|  
  
 ![](../Image/prn03.gif "prn03")  
Print output from data in the preceding table. ABCD on the top print line and WXYZ indented on the lower line.  
  
## See Also  
 [Host Print Service (Operations)](../Topic/Host%20Print%20Service%20\(Operations\)1.md)