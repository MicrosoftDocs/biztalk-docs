---
title: Troubleshoot and known issues with the BizTalk RosettaNet Accelerator (BTARN) install on BizTalk Server | Microsoft Docs"
description: Recommendations for installing SQL, the service account for the host instances, and known errors with the BTARN installation in BizTalk Server
ms.date: "06/08/2017"
ms.prod: "biztalk-server"

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
---


# Troubleshoot the installation and see the known install issues


## Do not install SQL Server on the domain controller computer  
 If you install SQL Server on the same computer as your domain controller computer, it returns the following error message when it is trying to create the SQL send ports:  

```
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500.  
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500  
```

> [!IMPORTANT]
>  Do not install SQL Server on the domain controller computer.  

## Service account for the application pools must be the same as the service account for the Isolated Host and Host instances  
 If the service account set for the BTARN application pools is different from the Isolated Host account, BTARN does not process incoming messages correctly. When the receive .aspx page calls the pipeline, the pipeline does not have access to the appropriate certificates. Therefore, it does not decrypt the incoming message or validate the signature. Also, it won't be able to access the MessageBox database.  


## Known install issues


### BTARN HTTP Front End Feature configuration fails  
 **Problem**  

 If you perform a custom installation to install only the BTARN HTTP Front End feature, BTARN configuration may fail with the following error after setup has completed: 

`Failed to create object for feature: WebApp`  

 **Resolution**  

Manually copy files and reconfigure: 

1. Copy the following two files from an BizTalk Server computer to the computer on which you installed the BTARN HTTP Front End feature:

   - Microsoft.VC80.ATL.manifest  

   - atl80.dll  

     If Visual Studio is installed on the same computer as BizTalk Server, the source folder for the two files is <*drive*>:\Program Files\Microsoft Visual Studio <version\>\VC\redist\x86\Microsoft.VC100.ATL.  

     If Visual Studio is not installed on the same BizTalk Server computer, the source folder for the two files is under <*drive*>:\WINDOWS\WinSxS.  

2. Add the copied files to the computer on which you installed BTARN HTTP Front End feature. By default, copy the files to <*drive*>:\Program Files\Microsoft BizTalk Accelerator for RosettaNet.  

3. After you have copied the files to the HTTP Front End computer, run **Configuration.exe** again.  

### Some BTARN Assemblies stay in GAC after uninstalling  
 **Problem**  

 When you uninstall BTARN, some assemblies remain in the global assembly cache (GAC).  

 **Resolution**  

 Remove the assemblies from the GAC before reinstalling BTARN.  

 Use the **BtarnClean** utility from the SDK to remove the assemblies. The utility performs the following actions:  

- Stops and unenlists all the BTARN orchestrations.  

- Stops and deletes all the associated ports.  

- Undeploys all the Microsoft.Solutions.BTARN.* assemblies.  

  After running the utility, if there are assemblies remaining in the GAC, open Windows Explorer, go to the "C:\Windows\Assembly" folder, and then manually delete all assemblies starting with Microsoft.Solutions.BTARN.  

### Service Unavailable error on 64-bit OS
 **Problem**  

 You may get a `Service Unavailable` error when trying to access the BTARN HTTP receive location on 64-bit Windows operating systems.  

 **Cause**  

 This issue can be caused by the "RPCProxy.dll" ISAPI filter.  

 **Resolution**  

Remove references to the RPC proxy ISAPI filter and restart IIS:

1.  In Internet Information Services (IIS) Manager, right-click **Web Sites**, and then click **Properties**.  

2.  In the **Web Site Properties** dialog box, click the **ISAPI filters** tab, remove **RPC Proxy** filter, and then click **OK**.  

3.  Restart IIS.  

4.  After you have restarted IIS, try accessing http://localhost. You should get the 400 message back from the Internet browser.  

### SQL Server Mixed Mode not supported  
BTARN does not support SQL Server in mixed mode.  

### Run setupx64.bat to set up the double action PIPAutomation orchestration sample 

Run setupx64.bat in \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction folder to set up the Double Action PIPAutomation Orchestration sample.

### Download the BTARN Setup File from the Web to a Temp Folder  
 **Problem**  

 If you download the BTARN self-extracting executable file from the Web, and save it to the BizTalk Server root folder, when you attempt to run the executable, the BizTalk **Setup Wizard** runs, instead of the BTARN Setup wizard.  

 **Resolution**  

 Download the BTARN self-extracting executable, and save the file to a temp folder.
