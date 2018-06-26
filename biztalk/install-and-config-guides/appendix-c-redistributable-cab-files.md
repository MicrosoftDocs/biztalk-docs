---
title: "Appendix C: Redistributable CAB Files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2049d61-e169-4b30-869a-33d5af097941
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix C: Redistributable CAB Files
These CAB files are used by the BizTalk Server setup.

## BizTalk 2016 CAB files

|Language|Download Link|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2016: [http://go.microsoft.com/fwlink/p/?LinkId=746413](http://go.microsoft.com/fwlink/p/?LinkId=746413)</li><li>Windows Server 2012 R2: [http://go.microsoft.com/fwlink/p/?LinkId=746412](http://go.microsoft.com/fwlink/p/?LinkId=746412)</li><li>Windows 10: [http://go.microsoft.com/fwlink/p/?LinkId=746408](http://go.microsoft.com/fwlink/p/?LinkId=746408)</li><li>Windows 8.1: [http://go.microsoft.com/fwlink/p/?LinkId=746411](http://go.microsoft.com/fwlink/p/?LinkId=746411)</li></ul></li><li>**X32**<br /><br /><ul><li>Windows 10: [http://go.microsoft.com/fwlink/p/?LinkId=746409](http://go.microsoft.com/fwlink/p/?LinkId=746409)</li><li>Windows 8.1: [http://go.microsoft.com/fwlink/p/?LinkId=746410](http://go.microsoft.com/fwlink/p/?LinkId=746410)</li></ul></li></ul>|  

> [!NOTE] 
> Windows 10 and Windows Server 2016 use the same CAB files as Windows 8.1 and Windows Server 2012 R2. As a reuslt, they have the the same file name.

## BizTalk 2013 R2 and 2013 CAB files  

|Language|Download Link|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2012: [http://go.microsoft.com/fwlink/p/?LinkId=269616](http://go.microsoft.com/fwlink/p/?LinkId=269616)</li><li>Windows Server 2008: [http://go.microsoft.com/fwlink/p/?LinkId=269613](http://go.microsoft.com/fwlink/p/?LinkId=269613)</li><li>Windows 8: [http://go.microsoft.com/fwlink/p/?LinkId=269615](http://go.microsoft.com/fwlink/p/?LinkId=269615)</li><li>Windows 7: [http://go.microsoft.com/fwlink/p/?LinkId=269614](http://go.microsoft.com/fwlink/p/?LinkId=269614)</li></ul></li><li>**X32**<br /><br /> <ul><li>Windows 8: [http://go.microsoft.com/fwlink/p/?LinkId=269612](http://go.microsoft.com/fwlink/p/?LinkId=269612)</li><li>Windows 7: [http://go.microsoft.com/fwlink/p/?LinkId=269611](http://go.microsoft.com/fwlink/p/?LinkId=269611)</li></ul></li></ul>|  

## Important info

- SQL XML may have its own software requirements (such as `.NET Framework 3.5` and `.NET Framework 2.0`), which are not included in the CAB file. If the BizTalk Server has internet access, the SQL XML software requirements may automatically install. If the BizTalk Server does not have internet access, then manually install the SQL XML software requirements.

- The CAB file install paths are also listed in the **Setup.xml** file in the install folder ([!INCLUDE[btsBizTalkServerPathx64_md](../includes/btsbiztalkserverpathx64-md.md)]\<your version\>).

- Some software required by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on your computer when you run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup.  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup gives you the option of downloading software prerequisites from the Web or extracting them from CAB files. If you choose the CAB files, download the CAB files before running setup.  

- You cannot use CAB files from previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You must download the CAB files from the links in the table.  

- You cannot download the CAB files through a Telnet session.  
