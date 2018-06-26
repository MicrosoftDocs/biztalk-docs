---
title: "MsSna_PrintSession Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c13682d-4764-402c-856f-e740be557565
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_PrintSession Class
A base class for a print session on a Print service.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PrintSession : MsSna_Config  
{  
   String Name;  
   String Service;  
   String Comment;  
   String StatusText;  
   sint16 Activation;  
   sint16 CodePage;  
   sint16 CodePageLanguage;  
   String PrinterDeviceName;  
   String CodePageCustomFile;   
   String PrinterFile;  
   boolean PrintToFile;  
   String FaceName;  
   boolean FaceNameOverride;  
   sint32 LeftMargin;  
   sint32 RightMargin;  
   sint32 TopMargin;  
   sint32 BottomMargin;  
   boolean MarginOverride;  
   boolean UniqueExtension;  
   String PDTFile;  
   boolean CheckPDTFile;  
   String Filter;  
   boolean bFilter;  
   sint16 FontSize;  
   sint16 SessionType;  
   sint16 LinesPerInch;  
   sint16 CharsPerLine;  
   boolean IgnoreTransparentSections;  
   boolean NoHorizontalScaling;  
   boolean NoVerticalScaling;  
   boolean LPIOverride;  
   boolean PageSetupOverride;  
};  
```  
  
#### Parameters  
 **Name**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(32), TOUPPERCASE**Access Type: Read/Write  
  
 The session name, which distinguishes different printers on the network.  
  
 **Service**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(20)</strong>Access Type: Read/Write  
  
 The SNA service to which the print session belongs.  
  
 **Comment**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **StatusText**  
 Data Type: **String** Access Type: Read/Write  
  
 The status of the print session.  
  
 **Activation**  
 Data Type: **String** Access Type: Read/Write  
  
 The print session activation. The following table describes the possible values for **Activation**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Automatic. Activates the print session automatically when the Host Print service is started|  
|1|Manual. Activates the print session manually.|  
  
 **CodePage**  
 Data Type: **sint16**Access Type: Read/Write  
  
 A value that indicates whether a standard language code or a custom code page will be used. The following table describes the possible values for **CodePage**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Language|  
|1|Custom|  
  
 **CodePageLanguage**  
 Data Type: **sint16**Access Type: Read/Write  
  
 The code page to be used in the print session. For more information about the possible values for **CodePageLanguage**, see the **Remarks** section.  
  
 **PrinterDeviceName**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(256)</strong>Access Type: Read/Write  
  
 The name of the destination printer.  
  
 **CodePageCustomFile**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(256)</strong>Access Type: Read/Write  
  
 The file name if a custom code page is to be used.  
  
 **PrinterFile**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(256)</strong>Access Type: Read/Write  
  
 The name of the file. Valid only when printing to a file.  
  
 **PrintToFile**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the print job will be sent to a file; otherwise, **false**. Note that you must still configure a destination printer.  
  
 **FaceName**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(31)</strong>Access Type: Read/Write  
  
 The name of the face.  
  
 **FaceNameOverride**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to override the host commands; otherwise, **false**.  
  
 **LeftMargin**  
 Data Type: **sint32** Qualifiers: <strong>MINVALUE(0), MAXVALUE(255)</strong>Access Type: Read/Write  
  
 The left margin, in inches.  
  
 **RightMargin**  
 Data Type: **sint32** Qualifiers: **MINVALUE(0), MAXVALUE(255)** Access Type: Read/Write  
  
 The right margin, in inches.  
  
 **TopMargin**  
 Data Type: **String** Qualifiers: **MINVALUE(0), MAXVALUE(255)** Access Type: Read/Write  
  
 The top margin, in inches.  
  
 **BottomMargin**  
 Data Type: **sint32** Qualifiers: <strong>MINVALUE(0), MAXVALUE(255)</strong>Access Type: Read/Write  
  
 The bottom margin, in inches.  
  
 **MarginOverride**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to override the host margin commands; otherwise, **false**.  
  
 **UniqueExtension**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to instruct the print service to give each file a unique extension when printing a file.  
  
 **PDTFile**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(256)</strong>Access Type: Read/Write  
  
 A PDT file used to format the print job.  
  
 **CheckPDTFile**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that a PDT file will be used to format the print job; otherwise, **false**.  
  
 **Filter**  
 Data Type: **String** Qualifiers: <strong>MAXLEN(256)</strong>Access Type: Read/Write  
  
 The filter DLL to be used to filter the printer data stream.  
  
 **bFilter**  
 Data Type: **Boolean** Qualifiers: **QualiferValueHere** Access Type: Read/Write  
  
 **true** to indicate that a filter DLL will be used to filter the printer data stream; otherwise, **false**.  
  
 **FontSizeOverride**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to override the host font size commands.  
  
 **FontSize**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(3276)** Access Type: Read/Write  
  
 The font size to be used when printing.  
  
 **SessionType**  
 Data Type: **sint16** Access Type: Read/Write  
  
 A value that indicates whether this is an APPC or 3270 print session. The following table describes the possible values for **SessionType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|APPC|  
|1|3270|  
  
 **LinesPerInch**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(12)** Access Type: Read/Write  
  
 The number of lines per inch to be printed.  
  
 **CharsPerLine**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The number of characters per line to be printed.  
  
 **IgnoreTransparentSections**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to ignore sections of the print data stream that have been marked as Transparent; otherwise, **false**. This value is valid only when using a PDT file to format the data.  
  
 **NoHorizontalScaling**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to turn off off the horizontal scaling feature of the printer driver; otherwise, **false**.  
  
 **NoVerticalScaling**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to turn off off the vertical scaling feature of the printer driver; otherwise, **false**.  
  
 **LPIOverride**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable host commands for lines per inch to be overridden; otherwise, **false**.  
  
 **PageSetupOverride**  
 Data Type: **String** Access Type: Read/Write  
  
 The override for the page setup.  
  
## Remarks  
 The following table describes the possible values for **CodePageLanguage**.  
  
|||  
|-|-|  
|0|Afrikaans[500]|  
|1|Albanian[870]|  
|2|Arabic (Algeria)[420]|  
|3|Arabic (Kingdom of Bahrain)[420]|  
|4|Arabic (Egypt)[420]|  
|5|Arabic (Iraq)[420]|  
|6|Arabic (Jordan)[420]|  
|7|Arabic (Kuwait)[420]|  
|8|Arabic (Lebanon)[420]|  
|9|Arabic (Libya)[420]|  
|10|Arabic (Morocco)[420]|  
|11|Arabic (Oman)[420]|  
|12|Arabic (Qatar)[420]|  
|13|Arabic (Saudi Arabia)[420]|  
|14|Arabic (Syria)[420]|  
|15|Arabic (Tunisia)[420]|  
|16|Arabic (U.A.E.)[420]|  
|17|Arabic (Yemen)[420]|  
|18|Basque[284]|  
|19|Belarusian[1025]|  
|20|Bulgarian[1025]|  
|21|Catalan[284]|  
|22|Chinese (PRC)[935]|  
|23|Chinese (Singapore)[935]|  
|24|Chinese (Hong Kong)[937]|  
|25|Chinese (Macau)[937]|  
|26|Chinese (Taiwan)[937]|  
|27|Croatian[870]|  
|28|Czech[870]|  
|29|Danish[277]|  
|30|Dutch (Belgium)[500]|  
|31|Dutch (Standard)[037]|  
|32|English (Australian)[037]|  
|33|English (Belize)[500]|  
|34|English (Canadian)[037]|  
|35|English (Caribbean)[500]|  
|36|English (Ireland)[285]|  
|37|English (Jamaica)[500]|  
|38|English (New Zealand)[037]|  
|39|English (South Africa)[037]|  
|40|English (Trinidad)[500]|  
|41|English (United Kingdom)[285]|  
|42|English (United States)[037]|  
|43|Estonian[1112]|  
|44|Faeroese[277]|  
|45|Finnish[278]|  
|46|French (Belgium)[500]|  
|47|French (Canadian)[037]|  
|48|French (Luxembourg)[500]|  
|49|French (Standard)[297]|  
|50|French (Swiss)[500]|  
|51|German (Austrian)[273]|  
|52|German (Liechtenstein)[500]|  
|53|German (Luxembourg)[500]|  
|54|German (Standard)[273]|  
|55|German (Swiss)[500]|  
|56|Greek[423]|  
|57|Greek (Modern)[875]|  
|58|Hebrew[424]|  
|59|Hungarian[870]|  
|60|Icelandic[871]|  
|61|Indonesian[037]|  
|62|Italian[280]|  
|63|Italian (Swiss)[500]|  
|64|International[500]|  
|65|Japanese (Extend Katakana)[930]|  
|66|Japanese (English-lower)[931]|  
|67|Japanese (Extend English)[939]|  
|68|Japanese (Katakana)[290]|  
|69|Korean[933]|  
|70|Latvian[1112]|  
|71|Lithuanian[1112]|  
|72|Macedonian[1025]|  
|73|Malay[037]|  
|74|Norwegian (Bokmal)[277]|  
|75|Norwegian (Nynorsk)[277]|  
|76|Polish[870]|  
|77|Portuguese (Brazil)[037]|  
|78|Portuguese (Portugal)[037]|  
|79|Romanian[870]|  
|80|Russian[880]|  
|81|Serbian (Cyrillic)[1025]|  
|82|Serbian (Latin)[870]|  
|83|Slovak[870]|  
|84|Slovenian[870]|  
|85|Spanish (Argentina)[284]|  
|86|Spanish (Bolivia)[284]|  
|87|Spanish (Chile)[284]|  
|88|Spanish (Columbia)[284]|  
|89|Spanish (Costa Rica)[284]|  
|90|Spanish (Dominican Rep.)[284]|  
|91|Spanish (Ecuador)[284]|  
|92|Spanish (El Salvador)[284]|  
|93|Spanish (Guatemala)[284]|  
|94|Spanish (Honduras)[284]|  
|95|Spanish (Mexico)[284]|  
|96|Spanish (Modern Sort)[284]|  
|97|Spanish (Nicaragua)[284]|  
|98|Spanish (Panama)[284]|  
|99|Spanish (Paraguay)[284]|  
|100|Spanish (Peru)[284]|  
|101|Spanish (Puerto Rico)[284]|  
|102|Spanish (Trad. Sort)[284]|  
|103|Spanish (Uruguay)[284]|  
|104|Spanish (Venezuela)[284]|  
|105|Swedish[278]|  
|106|Thai[838]|  
|107|Turkish[905]|  
|108|Turkish (Latin-5)[1026]|  
|109|Ukrainian[1025]|  
|110|Danish (Euro)[1142]|  
|111|English (Canadian) (Euro)[1140]|  
|112|English (United Kingdom) (Euro)[1146]|  
|113|English (United States) (Euro)[1140]|  
|114|Finnish (Euro)[1143]|  
|115|French (Standard) (Euro)[1147]|  
|116|German (Standard) (Euro)[1141]|  
|117|Icelandic (Euro)[1149]|  
|118|International (Euro)[1148]|  
|119|Italian (Euro)[1144]|  
|120|Latin-1 Open System (Euro)[924]|  
|121|Norwegian (Bokmal) (Euro)[1142]|  
|122|Norwegian (Nynorsk) (Euro)[1142]|  
|123|Spanish (Trad. Sort) (Euro)[1145]|  
|124|Swedish (Euro)[1143]|  
|125|Latin-1 Open System[1047]|  
|126|English (Australian) (Euro)[1140]|  
|127|French (Canadian) (Euro)[1140]|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)