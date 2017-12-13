---
title: "3270 Session1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNAPRINT_Session_3270"
ms.assetid: fc55555e-8aa9-495e-b219-42098bc98518
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# 3270 Session
The following tabs are available on the Print Session 3270 Properties sheet:  
  
## Print Session Properties: General  
 **Session Name**  
 To print 3270 jobs, you must define the session name, which is a descriptive name to distinguish different printers on the network.  
  
 **Comment**  
 Optionally, type a comment of 25 characters or less.  
  
 **Session Activation**  
 Click **Manual** to activate the print session manually, or **Automatic** to activate the print session automatically when the Host Print service is started.  
  
 **Host Code Page**  
 Click **Language**, and then select a **languagecode** from the drop-down list.  
  
 If your language code does not appear in the drop-down list, click **Custom**, then click the **File** button. The **Select Custom Page File** dialog box appears. Select your custom code page and click **Open**.  
  
> [!NOTE]
>  The custom page support in Host Print service provides Arabic and Hebrew code page support for left-to-right output only. The Host Print service does not support bi-directional data streams from right to left.  
  
 **Destination**  
 The default printer should appear in the box. Otherwise, click **Printer** to open the **Print Setup** dialog box. Make your selections and click **OK**.  
  
 Click **File** to send your job to a file. Check **Unique** to activate the **Reset** button. This feature allows you to reset the print job sequential numbering scheme (for example, when the number gets too high). Click **Reset**, and then click **Yes** to reset to the printer file extension numbering.  
  
> [!NOTE]
>  You need to select a printer driver to print to a file. Select a valid printer driver, then select File in the Destination box. Otherwise, you get an error message.  
  
## Print Session Properties: 3270  
 **LU Name**  
 Choose a **3270 printer LU** for the print session from the **LU Name** drop-down list. The drop-down list shows all of the LUs in an SNA Subdomain. If no 3270 printer LUs appear, you need to define one.  
  
 **Job Termination When**  
 Set job termination to either When End Bracket Received or When Unbind Received.  
  
 Selecting **When End Bracket Received** means the Host Print service will treat receiving the End Bracket notification from the host as an indication that the job is complete. Otherwise, the Print service defaults to spooling the job until the session ends: **When Unbind Received**.  
  
> [!NOTE]
>  If the host application sends print jobs that comprise multiple SNA brackets, set job termination to When End Bracket Received.  
  
 **Job Timeout**  
 To set a parameter for terminating print jobs, click the **Timeout Job After** box. Click the **Seconds Inactivity** up and down buttons to set the time limit for terminating print jobs. In some cases, an LU 3 print job is sent down from the host over an extended period of time. Selecting a Job Timeout ensures that the portions of the job are regularly form-fed. This option also provides normal timeout functionality for other 3270 print jobs.  
  
 **Monitor Job**  
 Click **Request Definite Response** if you want to invoke an advanced feature for applications that require a high level of assurance that a job completed. This feature sends a message to the host stating that the print job completed.  
  
> [!NOTE]
>  If you select the Request Definite Response feature, the host job must mark the data as RQD (definite response required).  
  
## Print Session Properties: Job Format  
 **Do Not Format Print Job**  
 Do Not Format Print Job allows print jobs that are formatted with host software to bypass the Microsoft® Windows®-based printing format system. The Windows-based Host Print service treats all received data as transparent. All data is passed directly to the printer.  
  
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
  
 Click **Printer Language is Hewlett-Packard (HP) PCL** if your PDT contains PCL commands. Limited support for Manager-defined font, margins and paper setup settings is automatically supported for HP (PCL), with full support available for customizing the Printer Definition File.  
  
 **Font**  
 To make changes to the font, click **Font**. Click the **Font** button. Make your selections in the Windows-based **Font** dialog box,and then click **OK**.  
  
 **Use Fixed Font Size**  
 Select the **Use Fixed Font Size** to select a user-defined font size. When this box is checked, the Host Print service will use the configured point size regardless of whether the data will fit (it will be clipped to fit the page if it is too large). When this option is selected, the Horizontal and Vertical scaling options on the **Advanced** tab are not available.  
  
## Print Session Properties: Page Layout  
 All these options are automatically available using the Windows GDI. Supporting these options using a PDT file may require extra configuration.  
  
### Horizontal Controls  
 **Characters per line**  
 The default is 132 characters per line. Type 80, 158, or another number for characters per line to change the default. The maximum line length is 255 characters.  
  
 Click **Override Host Commands** to force the specified settings and ignore host commands.  
  
### Vertical Controls  
 **Lines per Page**  
 Select **Lines Per Page** and then set the number of lines to be printed on each page.  
  
 **Lines Per Inch**  
 Select **Lines Per Inch** and then set either 6 or 8 lines per inch to set the default.  
  
 Click **Override Host Commands** to force the specified settings and ignore host commands.  
  
 **Margin Settings**  
 To change the margins, select **Margins**, and then click **Setup**. The **Page Setup** dialog box appears. Make your changes, and then click **OK**.  
  
 **Page settings**  
 Settings for Paper Source, Page Size, and Orientation are controlled from the Printer section. Click **Override Host Commands** to force the specified settings and ignore host commands.  
  
## Print Session Properties: Advanced  
 **Filter DLL**  
 Click **Filter DLL** to pass the printer data stream to a third-party or user-supplied DLL. Clicking **Filter** activates the **DLL File** button. The **Select Filter DLL** dialog box appears. Make your selection, then click **Open**.  
  
 **Ignore Transparent Sections for PDT Formatting**  
 Selecting this option will cause those sections of the print data stream that have been marked as transparent to be ignored when using a PDT file to format the data. Note, when using the GDI to format the data, transparent sections are automatically ignored. When such data is discarded, a log is written to the Event Log, containing the first 32 bytes of discarded data. This logging can be globally disabled from the Host Print service properties page.  
  
 **Do Not Scale Horizontally**  
 Selecting this option will turn off the horizontal scaling feature of the printer driver.  
  
 **Do Not Scale Vertically**  
 Selecting this option will turn off the vertical scaling feature of the printer driver.  
  
### 3270 Printing  
 **Transparency is ASCII**  
 Click **Transparency is ASCII** to indicate that transparent data from the host is in ASCII and needs no translation from EBCDIC to ASCII. Selecting **Transparency is ASCII** causes the Windows-based Host Print service to not put the received data through an EBCDIC to ASCII translation table before printing.  
  
 **Transparency Custom Byte**  
 **Transparency Custom Byte** indicates the character designated to start a sequence of transparent data (the transparent data may or may not be ASCII). The IBM standard is 0x35, but if the host print job uses another value (for example 0x36, and so on), then this should be specified here.  
  
 **No Line Formatting**  
 Prevents the SNA Print Service from inserting its own Carriage Return/Line Feed (CR/LF) according to the dimensions specified in the Default Page Width field (also on this property page). As No Line Formatting is a special case, this box is usually not checked. It is a useful option when using physical printers that do their own wrapping or are told to do their own wrapping with an Esc sequence. The Esc sequence that causes a printer to do its own End-of-line wrap on PCL printers is \<Esc>&s0C.  
  
 **Printer Time Out**  
 Default is 10 seconds. This parameter optimizes performance and system resources. If the printer is always available, system resources are consumed. However, if the printer is constantly being "opened" and "closed" with each print job sent, performance suffers. By setting the time out, the printer will remain available for jobs sent close together to improve performance, and yet "close" during non-busy times to free up resources.  
  
## See Also  
 [Character Tables](../core/character-tables2.md)   
 [Configuring Your Enterprise](../core/configuring-your-enterprise1.md)