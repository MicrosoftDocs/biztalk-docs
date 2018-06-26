---
title: "Restrictions when configuring the File adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [File adapters], restrictions"
  - "File adapters, restrictions"
ms.assetid: 8d8137a7-5b16-4ae3-a0a7-6d114324bdf3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restrictions when configuring the File adapter
Restrictions and rules when using the file adapter.

## File mask and file name gotchas

The file mask is a string that specifies the type of file that the File receive handler will pick up from the receive location. The file name is a string that specifies the name of the file where the File send handler will write the message.  
  
 The following restrictions apply to the file name and file mask properties:  
  
- Only one file mask or file name can be specified per receive location or send port.  
  
- The full path or part of the path along with the file mask or file name is not allowed. The file mask and file name always represent a name without the path.  
  
- The file mask and file name are not case-sensitive.  
  
- The file name cannot contain any of the following characters: \< \> : / &#124; " ? * ;  
  
- The file mask cannot contain any of the following characters: \< \> : / &#124; " ; 
  
- The following reserved device names cannot be used as the name of a file: CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, and LPT9. In addition, any combinations of these with extensions are not allowed.  
  
- Windows disk volumes use the 8.3 (8dot3) naming convention by default, which uses short and long file names. Non-system disk volumes disable the 8dot3 naming convention, and therefore only use long file names. 

  When 8dot3 is enabled, files and their file extensions get converted to a short name. For example, `testabcdefgh.docx` gets converted to `testab~1.doc`. Notice that file name is shortened, and the file extension is shortened from `.docx` to `doc`.

  This behavior impacts how the File adapter receives file. If a file mask is set to `*.xml`, then files matching both `*.xml` and `*.xmln` extensions are picked up. 

  To see if the 8dot3 naming convention is enabled on your disks, open a command prompt as Administrator, and type `fsutil 8dot3name query c:`, or `fsutil 8dot3name query d:`, and so on. Sample output looks like the following:

  ```
  C:\WINDOWS\system32>fsutil 8dot3name query c:
  The volume state is: 0 (8dot3 name creation is enabled).
  The registry state is: 2 (Per volume setting - the default).
    
  Based on the above two settings, 8dot3 name creation is enabled on c:
  ```
    
  The File adapter uses the [FindFirstFile function](https://msdn.microsoft.com/library/windows/desktop/aa364418(v=vs.85).aspx). This function includes search results that have the short and long file names. To see the short and long file names in a folder, open a command prompt, go to your folder, and type `dir /x`. In a command prompt, you can also type `dir c:\foldername /x`.
    
  If you change the 8dot3name setting on a volume, then new files use the new setting. Any existing files keep their names until they are moved. 
    
  To only pick up your intended files, and to get better performance (less overhead) during higher load, then it may be best to configure the File adapter to use a volume where 8dot3name is disabled. 
  
- The total length of the file path, file mask, and file name (without macro substitution) must not exceed 256 characters. (This is a restriction of the MessageBox database.)  
  
- The file path cannot begin with "`\\`?".  
  
- Mapped network drive letters cannot be used in the file path, because they are user session based.  
  
  The BizTalk Messaging Engine always validates the file name and file mask properties at design time by using the items previously listed. In addition, the File adapter validates the file name and file mask properties at run time if the adapter sends the message on a dynamic port.  
  
> [!NOTE]
>  The File adapter does not pick up system files or read-only files. Only disk-based files are picked up, and not device files.  

## Using macros in file names

You can use a predefined set of macros to dynamically create the files in which the File send handler writes messages. Before creating a file on the file system, the File send handler replaces all the macros in the file name with their individual values. You can use several different macros in one file name.  
  
 You can use the file name macros while configuring the File send handler using the BizTalk Explorer object model.  
  
 The File send handler does not replace the macros with a value if any of the following are true:  
  
- The corresponding system property is not set.  
  
- The macro is misspelled.  
  
- The value for the macro contains symbols that are not valid in the file name.  
  
  If any of these conditions occur, the File send handler leaves the macros in the file name untouched, for example Myfile_%MessageID%.xml.  
  
  The following table lists the supported macros and describes how the File send handler replaces them.  
  
|Macro name|Substitute value|  
|----------------|----------------------|  
|%datetime%|Coordinated Universal Time (UTC) date time in the format YYYY-MM-DDThhmmss (for example, 1997-07-12T103508).|  
|%datetime_bts2000%|UTC date time in the format YYYYMMDDhhmmsss, where sss means seconds and milliseconds (for example, 199707121035234 means 1997/07/12, 10:35:23 and 400 milliseconds).|  
|%datetime.tz%|Local date time plus time zone from GMT in the format YYYY-MM-DDThhmmssTZD, (for example, 1997-07-12T103508+800).|  
|%DestinationParty%|Name of the destination party. The value comes from the message context property **BTS.DestinationParty**.|  
|%DestinationPartyQualifier%|Qualifier of the destination party. The value comes from the message context property **BTS.DestinationPartyQualifier**.|  
|%MessageID%|Globally unique identifier (GUID) of the message in BizTalk Server. The value comes directly from the message context property **BTS.MessageID**.|  
|%SourceFileName%|Name of the file from which the File adapter read the message. The file name includes the extension and excludes the file path, for example, Sample.xml. When substituting this property, the File adapter extracts the file name from the absolute file path stored in the **FILE.ReceivedFileName** context property. If the context property does not have a value—for example, if a message was received on an adapter other than the File adapter—the macro will not be substituted and will remain in the file name as is (for example, C:\Drop\\%SourceFileName%). **Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.|  
|%SourceParty%|Name of the source party from which the File adapter received the message. **Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.|  
|%SourcePartyQualifier%|Qualifier of the source party from which the File adapter received the message. **Note:**  Correct implementation of this macro requires that the output message is the same message as the received message.|  
|%time%|UTC time in the format hhmmss.|  
|%time.tz%|Local time plus time zone from GMT in the format hhmmssTZD (for example, 124525+530).|  
  
 
## Receive folder and destination location properties gotchas

The file receive location is a string that contains a path to a folder on a file system or network share from which the File receive handler reads files. The file destination location is a string that contains a path to a folder on a file system or network share where the File send handler writes files.  
  
 The following restrictions apply to the receive folder and destination location properties:  
  
- Existence of the file path on a file system or network share is not required at the time when you specify the property in the user.  
  
- The file path must always be absolute.  
  
- You can specify the file path by using Universal Naming Convention (UNC) format (for example, \\\\<*server*\>\\<*share*\>).  
  
- If the file path is in UNC format, the server name must not contain the following characters: ` ~ ! @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> / ? ;  
  
- You cannot use parent (\\..\\) and current (\\.\\) folder symbols in any part of the file path.  
  
- The file path is not case-sensitive.  
  
- The file path cannot contain any of the following characters: \< \> : / &#124; " ? * ;  
  
- You cannot use the following reserved device names in the file path: CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, and LPT9.  
  
- Total length of file path, file mask, or file name (without macro substitution) must not exceed 256 characters. (The MessageBox database imposes this restriction.)  
  
- The File adapter does not support Unicode specification of the file path (for example, "\\\\?\\").  
  
  Restrictions on the receive folder property only:  
  
- Do not set the receive folder property to a folder that uses the Microsoft Windows NT Distributed File System with a symbolic link. If you are using Windows NT Distributed File System, you can only use folders with straight network paths in File adapter receive locations.  
  
- When documents are sent to a UNC path, and you have more than one server receiving documents at the receive location for the File adapter, only one server will pick up and process most of the documents sent to that UNC path. For more information about file renaming, see the File Receive Adapter section of [File Adapter](../core/file-adapter.md).  
  
  Restrictions on the send folder property only:  
  
- The file adapter may not have enough operating system resources to process all of the messages in a batch concurrently when running on a non-server operating system like Microsoft Windows Vista.  
  
  The File adapter validates the file path at design time by using the previously mentioned rules. In addition, the File adapter validates the message at run time if the adapter sends the message through a dynamic port with a File adapter.  
  
