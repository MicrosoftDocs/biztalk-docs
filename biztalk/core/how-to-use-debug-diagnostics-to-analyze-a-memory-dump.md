---
description: "Learn more about: How to Use Debug Diagnostics to Analyze a Memory Dump"
title: "How to Use Debug Diagnostics to Analyze a Memory Dump"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use Debug Diagnostics to Analyze a Memory Dump
The IIS Diagnostics **Debug Diagnostics Tool** includes a feature that can provide a basic analysis of a captured memory dump file. To perform an analysis of a memory dump file follow these steps.  
  
### To analyze the dump file  
  
1.  Launch the Debug Diagnostics tool from **Start**, **Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.  
  
2.  Click the **Advanced Analysis** tab.  
  
3.  Under **Available Analysis Scripts** click to select **Crash/Hang Analyzers** to analyze a crash/hang dump or click to select **Memory Pressure Analysis** to analyze a memory dump of a process suspected of leaking memory.  
  
4.  Click the **Add Data Files** button to browse to the generated dump file and click the **Open** button to add the dump file to the possible list of data files to be analyzed.  
  
5.  Click to select the dump file that was added.  
  
6.  Click the **Start Analysis** button.  
  
    > [!NOTE]
    >  The analyzer attempts to locate and download the appropriate symbol files from the internet if the symbol files are not installed on the local computer. If custom code is being executed in the BTSNTSvc.exe process, update the **Symbol Search Path For Debugging** option available in the **Folder And Search Paths** tab of the **Options & Settings** dialog to include the appropriate symbol files. Click the **Tools** menu and select **Options And Settings** to display the **Options & Settings** dialog.  
  
7.  Once the analysis is complete a report is generated in .mht file format and displayed in Internet Explorer. By default this report is saved to the \Program Files\IIS Resources\DebugDiag\Reports directory of the local computer.  
  
## See Also  
 [How to Capture a Memory Dump of a BizTalk Process](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)
