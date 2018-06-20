---
title: "Snacfg PrintSessionAPPC2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8eef1e4-3e49-4a00-a297-df7e64bc273a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Snacfg PrintSessionAPPC
## Purpose  
 Allows you to add, delete, modify, or view APPC print sessions defined in the Host Print Service.  
  
> [!NOTE]
>  Configuration settings specified with snacfg printsessionAPPC correspond to local print server setting configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath]  [configpath] printsessionAPPCnameservernamelocalLUname [options]  
[configpath] printsessionAPPCname [options]  
[configpath] printsessionAPPCname  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of APPC print sessions.  
  
 **/print**  
 Displays a list of the configuration settings of a print session. The displayed command does not contain the word **snacfg**, so that it can be redirected to a command file. Command files are discussed earlier in this section.  
  
 **/add**  
 Adds a print session to the Host Print Service. To configure the print session, you must specify the server name and the configured APPC local LU alias name after the **/add**. The required options are **/server:**<em>servername</em>and **/localLUalias:**<em>localLUname</em>  
  
 **/delete**  
 Deletes the printer session. To delete the print session, you must specify the server name and the configured local LU alias after the **/delete**.  
  
## Options for APPC Print Sessions  
 **/autoactivate:{ yes &#124; no }**  
 Specifies whether the printer session will automatically activate when Host Integration Server is started. The default is **yes**.  
  
 **/bestfit:{ yes &#124; no }**  
 Specifies whether to scale the output to the paper size. The default is **yes**.  
  
 **/codepage: {Country &#124; Custom}**  
 This defines the host code page language in which the print jobs are printed. The default is **Country** and the default language is **English (United States) [037]**. To change the default language, provide the number of the host code page of the country/region you want using the **/country** option.  
  
 If you want to use a custom file for the host code page, you must use **/customfile:**<em>text,</em> where the text value is the name of the file containing the specifications.  
  
 **/collate:{ yes &#124; no }**  
 Adds an option to collate pages sequentially.  
  
 **/color:{ yes &#124; no }**  
 For color printers, printing will be gray scale if nothing is selected.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the printer session. It can contain as many as 25 characters; enclose the comment in quotes.  
  
 **/country:** *value*  
 Specifies the language in which the print jobs are printed.  
  
 **/customfile:**" *text*"  
 Specifies the name of the file containing the custom language translation information. Use this option if you specify **/codepage:custom**.  
  
 **/devicename:**" *text*"  
 Specifies the name of the destination printer.  
  
 **/duplex:** *simplex &#124; horizontal &#124; vertical*  
 Specifies printing on two-sided paper.  
  
 **/filterfile:**" *text*"  
 This parameter is a defined programming API that allows you to pass the printer data stream to a third-party or user-supplied DLL. Enter the text of the file to which the printer data stream should go.  
  
 **/font:**" *text*"  
 Specifies the font to be used in the printer sessions. This can be any available font installed on the computer.  
  
 **/formname:** *string*  
 Specifies the name for the form.  
  
 **/margin:** *left, right, top, bottom*  
 Specifies the margins of the page, in inches, in the order of left, right, top, bottom. The default margins are 0".  
  
 **/orientation:** *portrait, landscape*  
 Specifies the page layout as portrait or landscape.  
  
 **/pagewidth:** *value (0-255)*  
 Specifies the width of page in characters.  
  
 **/papersize:** *value*  
 Specifies the size of the paper for printing.  
  
 **/paperlength:** *value*  
 Specifies the length of the paper for printing. The values for paperlength and paperwidth are in tenths of a millimeter, and override the papersize setting.  
  
 <strong>/paperwidth:</strong>v *alue*  
 Specifies the width of the paper. The values for paperlength and paperwidth are in tenths of a millimeter, and override the papersize setting.  
  
 **/pdtfile:**" *text*"  
 Specifies the name of a printer definition file.  
  
 **/provider:**" *text*"  
 This parameter maps to one of the two print provider DLLs (PPD3270.DLL or PPD5250.DLL) and tells Host Printer Service which DLL to load for the printer communications (ppd3270.dll or ppd5250.dll). The text for **snacfg printsessionappc** is PPD5250.  
  
 **/printtofile:**" *text*"  
 Specifies the name of a text file to which the output is to be sent. When information is entered into this parameter, the print job is saved into a file on the hard drive instead of sending it to the printer.  
  
 **/quality:** *high, medium, low, draft*  
 Specifies the quality of print.  
  
 **/scalefactor:** *value*  
 specifies the amount by which the printed output is to be scaled from the physical page size, divided by 100. For example, a scale factor of 50 would make the printed output half its normal size, 10 would be one tenth, and so on.  
  
 **/server:**" *text*"  
 Specifies the name of the server to which the session should attach. This is usually the name of an Host Integration Server computer that is running the Host Print Service in the subdomain. When **/add** is used, this option is required.  
  
 **/systemtype: {AS400 &#124; System36}**  
 Specifies the type of system being used.  
  
 **/truetype:** *bitmap, download, substitute*  
 Specifies TrueType fonts or substitutes.  
  
 **/uniqueextension:{ yes &#124; no }**  
 When the **/printtofile** option is used, the Host Print Service can generate a unique output file extension for each print job.  
  
 **/overridefontsize:{ yes &#124; no }**  
 Specifies whether or not the default font size can be overridden.  
  
 **/fontsize:**   
 ***value***  
 Specifies the size of the font (in points) used for output.  
  
 **/charset:**   
 ***value***  
 Specifies the font face used for output.  
  
 **/as400devicename:**" *text*"  
 Specifies the name of the AS/400 computer that will be sending the print job.  
  
 **/locallualias:**" *text*"  
 Specifies the previously configured local LU alias. This is a required parameter when using **/add**.  
  
 **/remotelualias:**" *text*"  
 Specifies the default remote APPC LU. If an LU is specified here, do not enter text into **/remotefqname**.  
  
 **/remotefqname:**" *text*"  
 Specifies the fully qualified name or alias of a remote APPC LU. The fully qualified name is the network name and LU name. If text is entered here, do not enter text into **/remotelualias**.  
  
 **/modename:**" *text*"  
 The default mode name is QPCSUPP. The other mode names available are: #INTERSC, BLANK, and QSERVER.  
  
 **/username:**" *text*"  
 Specifies the authorized user.  
  
 **/password:**" *text*"  
 Specifies the user password.  
  
 **/hostprinttransform:{ yes &#124; no }**  
 Enter *yes* to activate the Host Print Transform feature.  
  
 **/msgqname:**" *text*"  
 Specifies the qualified name of the message queue to which operational messages for this device are sent.  
  
 **/msglibname:**" *text*"  
 Specifies the library in which the message queue is located.  
  
 **/hostprintertype:**" *text*"  
 Specifies the type of host printer.  
  
 **/copies:**   
 ***value***  
 Specifies the number of copies to print.  
  
 **/papersrc1:{ continuous &#124; cut &#124; autocut }**  
 Specifies the type of paper used in the output device.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)