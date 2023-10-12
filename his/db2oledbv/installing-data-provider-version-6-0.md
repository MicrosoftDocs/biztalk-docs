---
description: "Learn more about: Installing Data Provider Version 6.0"
title: "Installing Data Provider Version 6.0"
ms.custom: ""
ms.date: "2/5/2020"
ms.prod: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing Data Provider Version 6.0
This topic provides instructions to install the Data Provider Version 6.0.


## Supported Operating Systems
 The Data Provider (32-bit x86 or 64-bit x64) will install on these Microsoft operating systems.

-   Windows Server 2019

-   Windows Server 2016

-   Windows Server 2012 R2

-   Windows Server 2012

-   Windows 10

-   Windows 8.1

-   Windows 8

-   Virtualization with Hyper-V

-   Virtualization with Windows Azure

## Supported OLE DB Data Consumers
 The Data Provider (32-bit x86 or 64-bit x64) is supported with these Microsoft OLE DB data consumers.

-   SQL Server 2019

-   SQL Server 2017

-   SQL Server 2016

-   SQL Server 2014

-   SQL Server Data Tools for SQL Server 2019

-   SQL Server Data Tools for SQL Server 2017

-   SQL Server Data Tools for SQL Server 2016

-   SQL Server Data Tools for SQL Server 2014

## Supported DB2 Servers
 The Data Provider supports these IBM relational database management systems, using the included Microsoft DRDA (Distributed Relational Database Architecture) Client, when connecting across a TCP/IP network.

-   IBM DB2 for z/OS 12.1

-   IBM DB2 for z/OS 11.1

-   IBM DB2 for z/OS 10.1

-   IBM DB2 for i 7.3

-   IBM DB2 for i 7.2

-   IBM DB2 for i 7.1

-   IBM DB2 for LUW 11.5

-   IBM DB2 for LUW 11

-   IBM DB2 for LUW 10.5

## Prerequisite Software
 The Data Provider requires the following software products as installation prerequisites.

-   Microsoft .NET Framework 4.6 [Web installer](https://go.microsoft.com/fwlink/p/?LinkId=528259) (https://go.microsoft.com/fwlink/p/?LinkId=528259) **OR** the [off-line installer](https://go.microsoft.com/fwlink/p/?LinkId=528233) (https://go.microsoft.com/fwlink/p/?LinkId=528233

-   Microsoft [Visual C++ 2013 Redistributable Package (x86)](https://aka.ms/vs2013runtimes)

-   Microsoft [Visual C++ 2013 Redistributable Package (x64)](https://aka.ms/vs2013runtimes)

    > **NOTE:** When installing on a 64-bit (x64) operating system, you must install both x86 and x64 of Visual Studio 2013 Redistributable Packages.

## Upgrade from Previous Version
 Microsoft OLE DB Provider for DB2 V 6.0 does not upgrade previous releases. If you have the following previous versions installed, then you must remove them prior to installing the Microsoft OLE DB Provider for DB2 V 6.0.

-   Microsoft OLE DB Provider for DB2 V1.0

-   Microsoft OLE DB Provider for DB2 V1.0 with SP1

-   Microsoft OLE DB Provider for DB2 V2.0

-   Microsoft OLE DB Provider for DB2 V3.0

-   Microsoft OLE DB Provider for DB2 V4.0

-   Microsoft OLE DB Provider for DB2 V5.0

 Prior to upgrading, Microsoft recommends that you consider the Microsoft SQL Server and IBM DB2 support provided by previous releases of the Microsoft OLE DB Provider for DB2.
 
### Previous Version Platform Support Matrix

|Version|DB2OLEDB 6.0|DB2OLEDB 5.0|DB2OLEDB 4.0|  
|-|-|-|-|
|SQL Server 2019|Yes|No|No|
|SQL Server 2017|Yes|No|No|
|SQL Server 2016|Yes|Yes|No|
|SQL Server 2014|No|Yes|No|
|SQL Server 2012|No|No|Yes|
|SQL Server 2018 R2|No|No|Yes|
|DB2 for z/OS 12|Yes|No|No|
|DB2 for z/OS 11|Yes|No|No|
|DB2 for z/OS 10|Yes|Yes|No|
|DB2 for z/OS 9|No|Yes|Yes|
|DB2 for z/OS 8|No|Yes|Yes|
|DB2 for i 7.3|Yes|No|No|
|DB2 for i 7.2|Yes|No|No|
|DB2 for i 7.1|Yes|Yes|Yes|
|DB2 for i 6.1|No|Yes|Yes|
|DB2 for i 5.4|No|Yes|Yes|
|DB2 for LUW 11.5|Yes|No|No|
|DB2 for LUW 11|Yes|No|No|
|DB2 for LUW V10.5|Yes|Yes|No|
|DB2 for LUW 10|Yes|Yes|No|
|DB2 for LUW 9.7|No|Yes|Yes|
|DB2 for LUW 9.5|No|No|Yes|
|DB2 for LUW 9.1|No|No|Yes|

## Install the Product  
 There are two options for installing the Data Provider, including interactive installation and unattended installation. The following steps guide you through interactive installation.  
  
1.  Go to the Microsoft Download Center to locate the [Feature Pack for SQL Server 2017](https://aka.ms/db2oledb).  
  
2.  Download either the x86 (32-bit) **DB2OLEDB6_x86.msi** or the x64 (64-bit) version **DB2OLEDB6_x64.msi** of installation program.  
  
3.  Double-click the **.msi** file to start the **Setup** program.  

4.  On the **License Agreement** page, review the license terms, click the **I accept the terms in the license agreement** option, and then click **Install**. 

    > **NOTE:** Optionally, on the **License Agreement** page, click **Advanced**, and then on the **Destination Folder** page click **Change**, then on the **Product Features** page click **Next**, and then click **Install**. 
  
5.  On the **Registration Information** page, enter your **Name** and **Company**, and then click **Next**.  
  
6. When prompted by Windows **User Account Control**, click **Yes**.  
  
7. On the **Progress** page, view the status of the installation process.  
  
8. On the **Completion** page, click **Finish**.  
  
## Install the product unattended  
 There are two options for installing the Service for DRDA, including interactive installation and unattended installation. The following steps guide you through unattended installation.  
  
1.  From a command prompt with administration privileges, locate the installation folder in which you downloaded the installation program, enter **DB2OLEDB6_x86.msi /quiet** or **DB2OLEDB6_x64.msi /quiet** depending on the processor architecture.  
  
3.  To verify the installation, locate the installed product in **C:\Program Files (x86)\Microsoft OLE DB Provider for DB2** or **C:\Program Files\Microsoft OLE DB Provider for DB2**.  
  
    > **NOTE:** Optionally, to generate a log, add **/l \<log file name>** to the command string. To verify the installation, enter **notepad \<log file name>**, and then click **Enter**.  
  
## Repair  
 You can use **Windows Programs and Features** to launch the Program Maintenance to repair the installation.  
  
1.  Click **Control Panel**, click **Programs**, and then click **Programs and Features**. The **Uninstall or change a program** dialog appears.  

2.  In the **Name** list, right click **Microsoft OLE DB Provider for DB2 Version 6.0**,and then click **Repair**.

3. When prompted by Windows **User Account Control**, click **Yes**.

4. On the **Progress** page, view the status of the repair process.

## Uninstall
 You can use Windows Programs and Features to remove the product.

1.  Click **Control Panel**, click **Programs**, and then click **Programs and Features**. The **Uninstall or change a program** dialog appears.

2.  In the **Name** list, right click **Microsoft OLE DB Provider for DB2 Version 6.0**,and then click **Uninstall**.

3. When prompted by Windows **Program and Features**, click **Yes**.

4. When prompted by Windows **User Account Control**, click **Yes**.

5. On the **Progress** page, view the status of the repair process.


## Uninstall the product unattended
 You can use an unattended command to uninstall the product.

1.  From a command prompt with administration privileges, locate the installation folder in which you downloaded the installation program, enter **DB2OLEDB6_x86.msi /uninstall /quiet** or **DB2OLEDB6_x64.msi /uninstall /quiet** depending on the processor architecture.

3.  To verify the removal, look in the installtion folder **C:\Program Files (x86)\Microsoft OLE DB Provider for DB2** or **C:\Program Files\Microsoft OLE DB Provider for DB2**

    > **NOTE:** Optionally, to generate a log, add **/l \<log file name>** to the command string. To verify the installation, enter **notepad \<log file name>**, and then click **Enter**.
