---
title: "APPC Session2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNAPRINT_Session_APPC"
ms.assetid: a8df5bfa-ac55-4bbf-9f34-d5a92cb60e63
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# APPC Session
The following tabs are available on the Print Session 3270 Properties sheet:  
  
## Print Session Properties: APPC  
 **Remote APPC LU**  
 Choose **Alias** or **Fully Qualified Name** to select another remote APPC LU.  
  
 You must supply either a **Remote APPC LU Alias** or a **Fully Qualified Name** before you can leave this page. If you want to use a **Fully Qualified Name**, you need to select a **Remote APPC LU Alias** first, then select a **Local LU Alias**. Then you must go back and change from the **Remote APPC LU Alias** to the **Remote APPC LU Fully Qualified Name**. If you select **Fully Qualified Name** first, the **Local LU Alias** does not get initialized.  
  
 Network Name + LU Name in NETNAME.LUNAME syntax (for example, APPN.NORTHB).  
  
 **Local LU Alias**  
 Select the local LU alias from the drop-down list.  
  
 **Mode Name**  
 The default mode name is QPCSUPP. Click the drop-down list arrow to make another selection. The choices are: **#INTERSC**, **BLANK**, **QPCSUPP**, **QSERVER**.  
  
 **AS/400 Device Name**  
 You must enter the name for the AS/400 printer device, which is a descriptive name that distinguishes different printers on the network.  
  
 **System Type**  
 Select the type of system you are printing from; either AS/400, System/36, AS/36.  
  
 **AS/400**  
  **Msg Queue Name**  
 Enter the qualified name of the message queue to which operational messages for this device are sent.  
  
 **Msg Lib Name**  
 Enter the name of the library in which the message queue is located.  
  
 **System/36, AS/36**  
  
## APPC Print Session Properties: Security  
 **User ID**  
 Type your **User ID**.  
  
 **Password**  
 Type your **Password**. Click tab to put the cursor in the **Confirm** password box.  
  
 **Confirm Password**  
 Type your password again and click **OK**.  
  
## Print Session Properties: Job Format  
 **Job**  
 Do Not Format Print Job allows print jobs that are formatted with host software to bypass the Windows-based printing format system. The Windows-based Host Print service treats all received data as transparent. All data is passed directly to the printer.  
  
 **HPT**  
 Displays the **Host Print Transform Properties** box, where you can designate the printer type and paper sources.  
  
 The Host Print Transform feature changes print data on the AS/400 to the ASCII format needed by a PC printer.  
  
 Select a manufacturer type and model number. If you cannot find the type and model number in the list you can type them in the box. If you do not know the manufacturer type and model number, see your system administrator or see the help on the AS/400.  
  
> [!IMPORTANT]
>  You must enter an asterisk "**\\***" before the manufacturer type and model number. Make sure there are no spaces between the asterisk, manufacturer type and model number, for example: *HPIIISI, or \*IBM3812.  
  
 **Format Print Job**  
 Print jobs from a host system can be formatted one of two ways:  
  
 **GDI**  
 The Windows Graphical Device Interface (GDI) is used to format the print job. SCS codes in the data are interpreted and represented, and the GDI automatically supports all the configurable options such as font, margins, duplex, paper-source, and so on. Transparent sections (for example, containing PCL escape sequences) are just ignored. When such data is discarded, a log is written to the Event Log, containing the first 32 bytes of discarded data. This logging can be globally disabled from the Host Print service properties page.  
  
 Selecting this option disables the Ignore **Transparent Sections for PDT Formatting** on the **Advanced** tab.  
  
> [!NOTE]
>  If your print job has a mixture of SCS codes and PCL escapes, then you should use a PDT. The PDT should contain mappings for the SCS code functionality, and the PCL escapes should pass directly to the printer without being mapped.  
  
 **PDT**  
 A Printer Definition Table (PDT) is used to specify the output format, control codes, and transfer of characters to a printer. When you use a PDT, the Windows based printer driver is not used. The PDT defines all information used to generate the print output. Click the **PDT File** button to select a compiled Printer Definition File.  
  
 To create a new PDT, you must first create a Printer Definition File (PDF), and then compile the PDF into a PDT. (If an uncompiled PDF file is selected, the compilation is performed automatically each time the print session is used. This feature has a performance overhead and is available mainly for ease of development). The PDF is a text file that defines macros and session parameters.  
  
 The PDT may override changes you make to **Font**, **Margins**, or **Page Setup**, although it is now possible to support these options in the PDT file. If you want to print in a particular font with a PDT, you should alter the startup sequence in the PDT to tell the printer which font you require. When a PDT file is used, Host Print service uses the definitions of NL, CR, FF, and LF from the PDT file to allow it to format the print job correctly.  
  
 Click **Printer Language is Hewlett-Packard (HP) PCL** if your PDT contains PCL commands. Limited support for Manager defined font, margins and paper setup settings is automatically supported for HP (PCL), with full support available for customizing the Printer Definition File.  
  
 **Font**  
 To make changes to the font, click **Font**. Click the **Font** button. Make your selections in the Windows-based **Font** dialog box,and then click **OK**.  
  
 **Use Fixed Font Size**  
 Select the **Use Fixed Font Size** to select a user defined font size. When this box is checked, the Host Print service will use the configured point size regardless of whether the data will fit (it will be clipped to fit the page if it is too large). When this option is selected, the Horizontal and Vertical scaling options on the **Advanced** tab are not available.  
  
## APPC Print Session Properties: Advanced  
 **Filter DLL**  
 Click **Filter DLL** to pass the printer data stream to a third-party or user-supplied DLL. Clicking **Filter** activates the **DLL File** button. The **Select Filter DLL** dialog box appears. Make your selection, then click **Open**.  
  
 **Ignore Transparent Sections for PDT Formatting**  
 Selecting this option will cause those sections of the print data stream that have been marked as Transparent to be ignored when using a PDT file to format the data. Note, when using the GDI to format the data, Transparent sections are automatically ignored. When such data is discarded, a log is written to the Event Log, containing the first 32 bytes of discarded data. This logging can be globally disabled from the Host Print service properties page.  
  
 **Do Not Scale Horizontally**  
 Selecting this option will turn off the horizontal scaling feature of the printer driver.  
  
 **Do Not Scale Vertically**  
 Selecting this option will turn off the vertical scaling feature of the printer driver.  
  
## Print LU Properties: General  
 **LU Number**  
 Enter the LU Number.  
  
 **LU Name**  
 Enter the LU Name.  
  
 **Connection**  
 The connection for this LU is shown. The connection cannot be changed here.  
  
 **Pool**  
 If the LU has already been assigned to a pool, the pool name appears here.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
 **Use Compression**  
 Selecting this option will compress the data stream and reduce the local area network traffic.  
  
 **User Workstation Secured**  
 Selecting this option allows only this workstation to access the Host LU.  
  
## TN3270 Properties: Settings  
 **Idle Timeout**  
 Specify time limits. If the session is inactive for this length of time, then TN3270 service disconnects the client computer.  
  
 **Init Status Delay**  
 Specify time limits. This is the delay between the time when TN3270 service connects to a host session and the time the TN3270 service starts updating the client computer screen. There are often a large number of startup messages when the TN3270 service first connects to a host session, and this option gives the user the opportunity not to receive them all.  
  
 **Message Close Delay**  
 Specify time limits. When TN3270 service forces a client computer to disconnect (for example, when the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] session to the host has been lost), it sends the client computer an error message to be displayed on the screen. This value specifies the time between sending the message to the client computer and closing the socket with the client computer (which causes some client computers to clear the screen, and so erase the message).  
  
 **Refresh Cycle Time**  
 Specify time limits. This is the delay between updates of the status on the display.  
  
 **Default RU Sizes - Inbound and Outbound**  
 This controls the RU size (SNA message size) used by the TN3270 service for logon messages to and from the host. The minimum value for inbound or outbound RU size is 256 bytes. If the host application sends large logon screens, these values should be increased.  
  
 **Certificate CN**  
 The common name of the certificate used if TLS/SSL is enabled.  
  
## See Also  
 [Configuring Your Enterprise](../core/configuring-your-enterprise1.md)