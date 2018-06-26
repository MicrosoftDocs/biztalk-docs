---
title: "ApplicationManager (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51ebe7a8-a0ca-4d2a-bf40-ec6421ba5a95
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ApplicationManager (BizTalk Server Sample)
The ApplicationManager sample demonstrates how to start or stop a  BizTalk application by using the administration objects.  

## Prerequisites  

- You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.  

- The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution. For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).  

## What This Sample Does  
 This sample demonstrates using the **BtsCatalogExplorer** and **Application** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to start and stop a deployed  BizTalk application. The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]. A Windows PowerShell example script is also included in this topic. The sample demonstrates the following operations:  

-   Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.  

-   Finding an application instance from  **BtsCatalogExplorer** based on application name.  

-   Submitting a start or stop command for the application.  

## Where To Find This Sample  
 The sample is located in the following SDK location:  

 \<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager  

 The following table shows the files in this sample and describes their purpose.  


|                                 File(s)                                 |                                                 Description                                                  |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                               Program.cs                                | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] source file for operations demonstrated in this sample. |
| ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo |                                  Solution and project files for the sample.                                  |

## Building and Running This Sample  

#### To build this sample  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ApplicationManager.sln.  

2. On the **Build** menu, click **Build Solution**.  

#### To run this sample  

1. Open a command window and navigate to the following folder:  

    \<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug  

2. Run the file ApplicationManager.exe providing the following two ordered command-line arguments:  

   - **\<start&#124;stop\>** First argument is the operation to be performed on the deployed application.  

   - **\<ApplicationName\>** Second argument is the name of the deployed application.  

     For example:  

   ```  
   ApplicationManager.exe stop MyBizTalkApp  
   ```  

    Running the sample with insufficient command-line parameters displays the usage syntax. For example:  

   ```  
   Usage:  

   ApplicationManager <start|stop> <Application Name>  

    Where:  
     <Application Name> = The name of the application that needs to be changed  

   Example: ApplicationManager start Application1  
   ```  

## Windows PowerShell Script Example  
 The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:  

```  
#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  

#=== Loop through applications in the catalog trying to find a name match ===#  

foreach($app in $Catalog.Applications)  
{  
    if ($($app.Name) -ieq $args[1])  
    {  

        #=== The first command-line argument should be "start" or "stop" ===#  

        if ($args[0] -ieq "start")  
        {  
            Write-Host `r`nIssuing start command to $app.Name...`r`n  
            $app.Start([Microsoft.BizTalk.ExplorerOM.ApplicationStartOption] "StartAll")  
            $Catalog.SaveChanges()  
        }  

        if ($args[0] -ieq "stop")  
        {  
            Write-Host `r`nIssuing stop command to $app.Name...`r`n  
            $app.Stop([Microsoft.BizTalk.ExplorerOM.ApplicationStopOption] "StopAll")  
            $Catalog.SaveChanges()  
        }  

    }  
}  
```  

 The script expects the same command-line arguments as the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] sample. Here is an example of running the Windows PowerShell script to start a deployed BizTalk application:  

```  
PS C:\> .\ApplicationManager.ps1 start MyBizTalkApp  

Issuing start command to MyBizTalkApp ...  
```  

## See Also  
 [Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md)