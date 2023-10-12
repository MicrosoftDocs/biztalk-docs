---
description: "Learn more about: Appendix C: Redistributable CAB Files"
title: "Appendix C: Redistributable CAB Files"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Appendix C: Redistributable CAB Files
These CAB files are used by the BizTalk Server setup.

## BizTalk 2016 CAB files

|Language|Download Link|
|--------------|-------------------|
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2016: [https://go.microsoft.com/fwlink/p/?LinkId=746413](https://go.microsoft.com/fwlink/p/?LinkId=746413)</li><li>Windows Server 2012 R2: [https://go.microsoft.com/fwlink/p/?LinkId=746412](https://go.microsoft.com/fwlink/p/?LinkId=746412)</li><li>Windows 10: [https://go.microsoft.com/fwlink/p/?LinkId=746408](https://go.microsoft.com/fwlink/p/?LinkId=746408)</li><li>Windows 8.1: [https://go.microsoft.com/fwlink/p/?LinkId=746411](https://go.microsoft.com/fwlink/p/?LinkId=746411)</li></ul></li><li>**X32**<br /><br /><ul><li>Windows 10: [https://go.microsoft.com/fwlink/p/?LinkId=746409](https://go.microsoft.com/fwlink/p/?LinkId=746409)</li><li>Windows 8.1: [https://go.microsoft.com/fwlink/p/?LinkId=746410](https://go.microsoft.com/fwlink/p/?LinkId=746410)</li></ul></li></ul>|

> [!NOTE]
> Windows 10 and Windows Server 2016 use the same CAB files as Windows 8.1 and Windows Server 2012 R2. As a result, they have the same file name.

## BizTalk 2013 R2 and 2013 CAB files

|Language|Download Link|
|--------------|-------------------|
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2012: [https://go.microsoft.com/fwlink/p/?LinkId=269616](https://go.microsoft.com/fwlink/p/?LinkId=269616)</li><li>Windows Server 2008: [https://go.microsoft.com/fwlink/p/?LinkId=269613](https://go.microsoft.com/fwlink/p/?LinkId=269613)</li><li>Windows 8: [https://go.microsoft.com/fwlink/p/?LinkId=269615](https://go.microsoft.com/fwlink/p/?LinkId=269615)</li><li>Windows 7: [https://go.microsoft.com/fwlink/p/?LinkId=269614](https://go.microsoft.com/fwlink/p/?LinkId=269614)</li></ul></li><li>**X32**<br /><br /> <ul><li>Windows 8: [https://go.microsoft.com/fwlink/p/?LinkId=269612](https://go.microsoft.com/fwlink/p/?LinkId=269612)</li><li>Windows 7: [https://go.microsoft.com/fwlink/p/?LinkId=269611](https://go.microsoft.com/fwlink/p/?LinkId=269611)</li></ul></li></ul>|

## Important info

- SQL XML may have its own software requirements (such as `.NET Framework 3.5` and `.NET Framework 2.0`), which are not included in the CAB file. If the BizTalk Server has internet access, the SQL XML software requirements may automatically install. If the BizTalk Server does not have internet access, then manually install the SQL XML software requirements.

- The CAB file install paths are also listed in the **Setup.xml** file in the install folder ([!INCLUDE[btsBizTalkServerPathx64_md](../includes/btsbiztalkserverpathx64-md.md)]\<your version\>).

- Some software required by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on your computer when you run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup.

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup gives you the option of downloading software prerequisites from the Web or extracting them from CAB files. If you choose the CAB files, download the CAB files before running setup.

- You cannot use CAB files from previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You must download the CAB files from the links in the table.

- You cannot download the CAB files through a Telnet session.
