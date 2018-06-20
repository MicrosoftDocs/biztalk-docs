---
title: "Snacfg PrintSession32702 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adddcd80-d5de-41d7-9654-8f16caaf45b6
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg PrintSession3270
## Purpose  
 Allows you to add, delete, modify, or view 3270 print sessions defined in the Host Print Service.  
  
> [!NOTE]
>  Configuration settings specified with snacfg printsession3270 correspond to local print server settings configured with the SNA Manager.  
  
> [!NOTE]
>  The /feedignorefinal option is no longer supported. By default, this value is enabled. A PDF file can be used to control this behavior if required.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath]  [configpath] printsession3270nameservernameLUname[options]  
[configpath] printsession3270name [options]  
[configpath] printsession3270name  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of 3270 print sessions.  
  
 **/print**  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 **/add**  
 Adds a print session to the Host Print Service. To configure the print session, you must specify the server name and the configured 3270 printer LU name after the **/add** using the **/server:**<em>servername</em> and **/luname:**<em>Luname</em> options.  
  
 **/delete**  
 Deletes the printer session. To delete the print session, you must specify the server name and the configured 3270 printer LU name after the **/delete**.  
  
## Options for 3270 Print Sessions  
 **/autoactivate:{ yes &#124; no }**  
 Specifies whether the printer session will automatically activate when [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is started. The default is yes.  
  
 **/bestfit:{ yes &#124; no }**  
 Specifies whether to scale the output to the paper size. The default is **yes**.  
  
 **/codepage: {Country &#124; Custom}**  
 This defines the host code page language in which the print jobs are output. The default is **Country** and the default language is **English (United States) [037]**. To change the default language, provide the number of the host code page of the country/region you want with the **/country** option.  
  
 If you want to use a custom file for the host code page, you must use **/customfile:**<em>text,</em> where the *text* value is the name of the file containing the specifications for the print job.  
  
 **Host Code Page Numbers and Corresponding Language**  
  
|Host Code Page Number|Language|  
|---------------------------|--------------|  
|0|"Afrikaans  [500]"|  
|1|"Albanian  [870]"|  
|2|"Arabic (Algeria)  [420]"|  
|3|"Arabic (Kingdom of Bahrain)  [420]"|  
|4|"Arabic (Egypt)  [420]"|  
|5|"Arabic (Iraq)  [420]"|  
|6|"Arabic (Jordan)  [420]"|  
|7|"Arabic (Kuwait)  [420]"|  
|8|"Arabic (Lebanon)  [420]"|  
|9|"Arabic (Libya)  [420]"|  
|10|"Arabic (Morocco)  [420]"|  
|11|"Arabic (Oman)  [420]"|  
|12|"Arabic (Qatar)  [420]"|  
|13|"Arabic (Saudi Arabia)  [420]"|  
|14|"Arabic (Syria)  [420]"|  
|15|"Arabic (Tunisia)  [420]"|  
|16|"Arabic (U.A.E.)  [420]"|  
|17|"Arabic (Yemen)  [420]"|  
|18|"Basque  [284]"|  
|19|"Belarusian  [1025]"|  
|20|"Bulgarian  [1025]"|  
|21|"Catalan  [284]"|  
|22|"Chinese (PRC)  [935]"|  
|23|"Chinese (Singapore)  [935]"|  
|24|"Chinese (Hong Kong SAR)  [937]"|  
|25|"Chinese (Macao SAR)  [937]"|  
|26|"Chinese (Taiwan)  [937]"|  
|27|"Croatian  [870]"|  
|28|"Czech  [870]"|  
|29|"Danish  [277]"|  
|30|"Dutch (Belgium)  [500]"|  
|31|"Dutch (Standard)  [037]"|  
|32|"English (Australian)  [037]"|  
|33|"English (Belize)  [500]"|  
|34|"English (Canadian)  [037]"|  
|35|"English (Caribbean)  [500]"|  
|36|"English (Ireland)  [285]"|  
|37|"English (Jamaica)  [500]"|  
|38|"English (New Zealand)  [037]"|  
|39|"English (South Africa)  [037]"|  
|40|"English (Trinidad)  [500]"|  
|41|"English (United Kingdom)  [285]"|  
|42|"English (United States)  [037]"|  
|43|"Estonian  [1112]"|  
|44|"Faeroese  [277]"|  
|45|"Finnish  [278]"|  
|46|"French (Belgium)  [500]"|  
|47|"French (Canadian)  [037]"|  
|48|"French (Luxembourg)  [500]"|  
|49|"French (Standard)  [297]"|  
|50|"French (Swiss)  [500]"|  
|51|"German (Austrian)  [273]"|  
|52|"German (Liechtenstein)  [500]"|  
|53|"German (Luxembourg)  [500]"|  
|54|"German (Standard)  [273]"|  
|55|"German (Swiss)  [500]"|  
|56|"Greek  [423]"|  
|57|"Greek (Modern)  [875]"|  
|58|"Hebrew  [424]"|  
|59|"Hungarian  [870]"|  
|60|"Icelandic  [871]"|  
|61|"Indonesian  [037]"|  
|62|"Italian  [280]"|  
|63|"Italian (Swiss)  [500]"|  
|64|"International  [500]"|  
|65|"Japanese (Extend Katakana)  [930]"|  
|66|"Japanese (English-lower)  [931]"|  
|67|"Japanese (Extend English)  [939]"|  
|68|"Japanese (Katakana)  [290]"|  
|69|"Korean  [933]"|  
|70|"Latvian  [1112]"|  
|71|"Lithuanian  [1112]"|  
|72|"Macedonian  [1025]"|  
|73|"Malay  [037]"|  
|74|"Norwegian (Bokmal)  [277]"|  
|75|"Norwegian (Nynorsk)  [277]"|  
|76|"Polish  [870]"|  
|77|"Portuguese (Brazil)  [037]"|  
|78|"Portuguese (Portugal)  [037]"|  
|79|"Romanian  [870]"|  
|80|"Russian  [880]"|  
|81|"Serbian (Cyrillic)  [1025]"|  
|82|"Serbian (Latin)  [870]"|  
|83|"Slovak  [870]"|  
|84|"Slovenian  [870]"|  
|85|"Spanish (Argentina)  [284]"|  
|86|"Spanish (Bolivia)  [284]"|  
|87|"Spanish (Chile)  [284]"|  
|88|"Spanish (Columbia)  [284]"|  
|89|"Spanish (Costa Rica)  [284]"|  
|90|"Spanish (Dominican Rep.)  [284]"|  
|91|"Spanish (Ecuador)  [284]"|  
|92|"Spanish (El Salvador)  [284]"|  
|93|"Spanish (Guatemala)  [284]"|  
|94|"Spanish (Honduras)  [284]"|  
|95|"Spanish (Mexico)  [284]"|  
|96|"Spanish (Modern Sort)  [284]"|  
|97|"Spanish (Nicaragua)  [284]"|  
|98|"Spanish (Panama)  [284]"|  
|99|"Spanish (Paraguay)  [284]"|  
|100|"Spanish (Peru)  [284]"|  
|101|"Spanish (Puerto Rico)  [284]"|  
|102|"Spanish (Trad. Sort)  [284]"|  
|103|"Spanish (Uruguay)  [284]"|  
|104|"Spanish (Venezuela)  [284]"|  
|105|"Swedish  [278]"|  
|106|"Thai  [838]"|  
|107|"Turkish  [905]"|  
|108|"Turkish (Latin-5)  [1026]"|  
|109|"Ukrainian  [1025]"|  
  
 **/collate:{ yes &#124; no }**  
 Adds an option to collate pages sequentially.  
  
 **/color:{ yes &#124; no }**  
 For color printers, printing will be gray scale if nothing is selected.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the printer session. It can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/copies:** *value*  
 Specifies the number of copies for printing.  
  
 **/country:** *value*  
 Specifies the language in which the print jobs are printed.  
  
 **/customfile:**" *text*"  
 Specifies the name of the file containing the custom language translation information. Use this option if you specify **/codepage:custom**.  
  
 **/devicename:**" *text*"  
 Specifies the name of the destination printer.  
  
 **/duplex:** *simplex &#124; horizontal &#124; vertical*  
 Specifies printing on two-sided paper.  
  
 **/filterfile:**" *text*"  
 The **/filterfile** is a defined programming API that allows you to pass the printer data stream to a third party or user supplied DLL. Enter text to signify where the printer data stream should go.  
  
 **/font:**" *text*"  
 Specifies the font to be used in the printer sessions. This can be any available font installed on the computer.  
  
 **/formname:** *string*  
 Specifies the name for the form.  
  
 **/margin:** *left, right, top, bottom*  
 Specifies the margins of the page in inches in the order of left, right, top, bottom. The default margins are 0".  
  
 **/orientation:** *portrait, landscape*  
 Specifies the page layout as portrait or landscape.  
  
 **/papersize:** *value*  
 Specifies the size of the paper for printing.  
  
 **Valid Values and Descriptions for Papersize**  
  
|Value|Constant Name (from wingdi.h)|Description|  
|-----------|-------------------------------------|-----------------|  
|1|DMPAPER_LETTER|Letter, 8.5" x 11"|  
|2|DMPAPER_LETTERSMALL|Letter Small, 8.5" x 11"|  
|3|DMPAPER_TABLOID|Tabloid, 11" x 17"|  
|4|DMPAPER_LEDGER|Ledger, 17" x 11"|  
|5|DMPAPER_LEGAL|Legal, 8.5" x 14"|  
|6|DMPAPER_STATEMENT|Statement, 5.5" x 8.5"|  
|7|DMPAPER_EXECUTIVE|Executive, 7.25" x 10.5"|  
|8|DMPAPER_A3|A3 Sheet, 297 x 420mm|  
|9|DMPAPER_A4|A4 Sheet, 210 x 297mm|  
|10|DMPAPER_A4SMALL|A4 Small Sheet, 210 x 297mm|  
|11|DMPAPER_A5|A5 Sheet, 148 x 210mm|  
|12|DMPAPER_B4|B4 Sheet, 250 x 354mm|  
|13|DMPAPER_B5|B5 Sheet, 182 x 257mm|  
|14|DMPAPER_FOLIO|Folio, 8.5" x 13"|  
|15|DMPAPER_QUARTO|Quarto, 215 x 275mm|  
|16|DMPAPER_10X14|10" x 14" Sheet|  
|17|DMPAPER_11X17|11" x 17" Sheet|  
|18|DMPAPER_NOTE|Note, 8.5" x 11"|  
|19|DMPAPER_ENV_9|#9 Envelope, 3.875" x 8.875"|  
|20|DMPAPER_ENV_10|#10 Envelope, 4.125" x 9.5"|  
|21|DMPAPER_ENV_11|#11 Envelope, 4.5" x 10.375"|  
|22|DMPAPER_ENV_12|#12 Envelope, 4.75" x 11"|  
|23|DMPAPER_ENV_14|#14 Envelope, 5" x 11.5"|  
|24|DMPAPER_CSHEET|C Sheet, 17" x 22"|  
|25|DMPAPER_DSHEET|D Sheet, 22" x 34"|  
|26|DMPAPER_ESHEET|E Sheet, 34" x 44"|  
|27|DMPAPER_ENV_DL|DL Envelope, 110 x 220mm|  
|28|DMPAPER_ENV_C5|C5 Envelope, 162 x 229mm|  
|29|DMPAPER_ENV_C3|C3 Envelope, 324 x 458mm|  
|30|DMPAPER_ENV_C4|C4 Envelope, 229 x 324mm|  
|31|DMPAPER_ENV_C6|C6 Envelope, 114 x 162mm|  
|32|DMPAPER_ENV_C65|C65 Envelope, 114 x 229mm|  
|33|DMPAPER_ENV_B4|B4 Envelope, 250 x 353mm|  
|34|DMPAPER_ENV_B5|B5 Envelope, 176 x 250mm|  
5|DMPAPER_ENV_B6|B6 Envelope, 176 x 125mm|  
|36|DMPAPER_ENV_ITALY|Italy Envelope, 110 x 230mm|  
|37|DMPAPER_ENV_MONARCH|Monarch Envelope, 3.875" x 7.5"|  
|38|DMPAPER_ENV_PERSONAL|6.75 Envelope, 3.625" x 6.5"|  
|39|DMPAPER_FANFOLD_US|US Standard Fanfold, 14.875" x 11"|  
|40|DMPAPER_FANFOLD_STD_GERMAN|German Standard Fanfold, 8.5" x 12"|  
|41|DMPAPER_FANFOLD_LGL_GERMAN|German Legal Fanfold, 8.5" x 13"|  
  
 **Additional values, supported by Windows**  
  
||||  
|-|-|-|  
|42|DMPAPER_ISO_B4|B4 (ISO) 250 x 353mm|  
|43|DMPAPER_JAPANESE_POSTCARD|Japanese Postcard 100 x 148mm|  
|44|DMPAPER_9X11|9" x 11"|  
|45|DMPAPER_10X11|10" x 11"|  
|46|DMPAPER_15X11|15" x 11"|  
|47|DMPAPER_ENV_INVITE|Envelope Invite 220 x 220mm|  
|48|DMPAPER_RESERVED_48|Reserved -- do not use|  
|49|DMPAPER_RESERVED_49|Reserved -- do not use|  
|50|DMPAPER_LETTER_EXTRA|Letter Extra, 9.275" x 12"|  
|51|DMPAPER_LEGAL_EXTRA|Legal Extra, 9.275" x 15"|  
|52|DMPAPER_TABLOID_EXTRA|Tabloid Extra, 11.69" x 18"|  
|53|DMPAPER_A4_EXTRA|A4 Extra, 9.27" x 12.69"|  
|54|DMPAPER_LETTER_TRANSVERSE|Letter Transverse, 8.275" x 11"|  
|55|DMPAPER_A4_TRANSVERSE|A4 Transverse, 210 x 297mm|  
|56|DMPAPER_LETTER_EXTRA_ TRANSVERSE|Letter Extra Transverse, 9.275" x 12"|  
|57|DMPAPER_A_PLUS|SuperA / A4, 227 x 356mm|  
|58|DMPAPER_B_PLUS|SuperB / A3, 305 x 487mm|  
|59|DMPAPER_LETTER_PLUS|Letter Plus, 8.5" x 12.69"|  
|60|DMPAPER_A4_PLUS|A4 Plus, 210 x 330mm|  
|61|DMPAPER_A5_TRANSVERSE|A5 Transverse, 148 x 210mm|  
|62|DMPAPER_B5_TRANSVERSE|B5 (JIS) Transverse, 182 x 257mm|  
|63|DMPAPER_A3_EXTRA|A3 Extra, 322 x 445mm|  
|64|DMPAPER_A5_EXTRA|A5 Extra, 174 x 235mm|  
|65|DMPAPER_B5_EXTRA|A5 Extra, 174 x 235mm|  
|66|DMPAPER_A2|A2, 420 x 594mm|  
|67|DMPAPER_A3_TRANSVERSE|A3 Transverse, 297 x 420mm|  
|68|DMPAPER_A3_EXTRA_TRANSVERSE|A3 Extra Transverse, 322 x 445mm|  
  
 **/paperlength:** *value*  
 Specifies the length of the paper for printing. The values for paperlength and paperwidth are in tenths of a millimeter, and override the papersize setting.  
  
 <strong>/paperwidth:</strong>value  
 Specifies the width of the paper. The values for paperlength and paperwidth are in tenths of a millimeter, and override the papersize setting.  
  
 **/pdtfile:**" *text*"  
 Specifies the name of a printer definition file.  
  
 **/provider:**" *text*"  
 This parameter maps to one of the two print provider DLLs (PPD3270.DLL or PPD5250.DLL) and tells the Host Printer Service which DLL to load to do the printer communications (ppd3270.dll or ppd5250.dll). The text for **snacfg printsession3270** is PPD3270.  
  
 **/printtofile:**" *text*"  
 Specifies the name of a text file to which the output is to be sent. When information is entered into this parameter, the print job is saved into a file on the hard drive instead of being sent to the printer.  
  
 **/quality:** *high, medium, low, draft*  
 Specifies the quality of print.  
  
 **/scalefactor:** *value*  
 Specifies the amount by which the printed output is to be scaled from the physical page size, divided by 100. For example, a scale factor of 50 would make the printed output half its normal size, 10 would be one tenth, and so on.  
  
 **/server:**" *text*"  
 Specifies the name of the server to which the session should attach. This is usually the name of an Host Integration Server computer that is running the Host Print Service in the subdomain. When **/add** is used, this option is required.  
  
 **/truetype:** *bitmap, download, substitute*  
 Specifies TrueType fonts or substitutes.  
  
 **/uniqueextension:{ yes &#124; no }**  
 When the **/printtofile** option is used, specifying YES enables the Host Print Service to generate a unique output file extension for each print job.  
  
 **/overridefontsize:{ yes &#124; no }**  
 Specifies whether or not the default font size can be overridden.  
  
 **/fontsize:**   
 ***value***  
 Specifies the size of the font (in points) used for output.  
  
 **/charset:**   
 ***value***  
 Specifies the font face used for output.  
  
 **/bypassgdi:{ yes &#124; no }**  
 This allows print jobs that are formatted with host software to bypass the Windows printing format system. All the data from the host is passed directly to the printer. The default is **no**.  
  
 **/charsperline:**   
 ***value***  
 Specifies the number of characters printed per line.  
  
 **/feedperjob:{ yes &#124; no }**  
 If set to **yes**, it will issue a form feed between each print job. The default is **no**.  
  
 **/feedignoreinitial:{ yes &#124; no }**  
 If set to **yes**, the beginning form feed in a print job will be ignored. The default is **no**.  
  
 **/jobtermination:{ EndBracket &#124; UnBind }**  
 The print job will terminate when either a **When End Bracket Received** or a **When Unbind Received** command is received by the printer. The default is **EndBracket**.  
  
 **/linespacing:**   
 ***value***  
 Specifies the  space (in points) between printed lines.  
  
 **/linesperinch:{ 6 &#124; 8 }**  
 This specifies the number of lines per inch (either six or eight) in the print job. The default is **6**.  
  
 **/linewrap:{ yes &#124; no }**  
 Specifies whether the text will automatically wrap at the end of a line.  
  
 **/luname:**" *text*"  
 The name of the configured 3270 printer LU. When **/add** is used, this option is required.  
  
 **/monitorjob:{ yes &#124; no }**  
 If **yes** is specified, this feature sends a message to the host computer stating that the print job is completed. The default is **no**.  
  
 **/pagewidth:{ 80 &#124; 132 &#124; 158 }**  
 Specifies the default page width in number of characters per line. The values can be 80, 132, or 158 characters. The default is 80.  
  
 **/skipblanklines:{ yes &#124; no }**  
 If there are blank lines in the print job, it will not print them if **yes** is specified. The default is **no**.  
  
 **/timeout:** *value*  
 Specifies the time limit, in seconds, for terminating print jobs.  
  
 **/transparencyascii:{ yes &#124; no }**  
 This sets a flag that indicates that the transparent data from the host is in ASCII format and does not need translation from EBCDIC. The default is **no**.  
  
 **/transparencycustom:** *value*  
 Specifies the custom byte that sends the data stream in transparent mode. The IBM standard value is 0x35, but if the host print job uses another value, such as 0x36, then this should be specified.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)