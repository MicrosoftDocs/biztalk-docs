---
title: "Sending or Receiving a File1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76ee1b4c-b967-41fa-a458-2732d61126f4
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Sending or Receiving a File
After you have defined the settings you need to transfer files, and selected the file to transfer, you can send a file to or receive a file from the host. To send or receive a file, you must supply certain configuration information. This information includes the host filename, host file type, host file mode, data set name, carriage return, whether you are appending to an existing file, EBCDIC conversion, and carriage return line feed.  
  
 **To send a file to the host or receive a file from the host**  
  
1.  After specifying the file, find the items that apply to your configuration, and supply the information as follows:  
  
     **Specify the host file type.** For CICS, select either ASCII File or Binary File.  
  
     **Host File Mode (VM/CMS)** Specify the host file mode, the specific minidisk where the user data resides. To find out the mode for a specific file, from an Client session, type the following command, substituting the name of the file for filename: list filename * \*.  
  
     In the resulting display, the third column contains the file mode. The default host file mode is A1.  
  
     **Data Set Name (TSO)** Specify the host data set name. Be sure to include the Member name, in parentheses, if you are sending to a host partitioned data set (PDS). The following is an example of a data set name for a PDSDEF_009:  
  
     PROJECT.GROUP.TYPE(MEMBER)  
  
     **Carriage Return (CICS)** Select the carriage return option for the file you are sending or receiving. Delete CR/LF removes all carriage return/line feed characters from the file sent to the host. No CR/LF leaves the carriage return/line feed characters in the file when transferring to the host. None of the Above uses the default implied by the type of file (ASCII or binary) being transferred. The default for ASCII (being converted to EBCDIC) is CR/LF. The default for binary is No CR/LF, and CRLFs will not be interpreted.  
  
     **Append to Existing File (send)** Select this check box to add new data to the end of an existing host file.  
  
     **Convert to EBCDIC (send)** Select this check box to convert from ASCII to EBCDIC.  
  
     **Convert from EBCDIC (receive)** Select this check box to convert from EBCDIC to ASCII. Use this option for text files rather than binary files.  
  
     **Delete Carriage Return/Line Feed CR/LF (send)** Select this check box to replace all CR/LF characters with end of record marks.  
  
     **Insert Carriage Return/Line Feed CR/LF (receive)** Select this check box to replace all end-of-record marks with CR/LF characters. Use this option for text files rather  than binary files.  
  
2.  Click **OK**. The 3270 Client begins the transfer.  
  
## See Also  
 [3270 Client](../core/3270-client2.md)