---
title: "Install the BizTalk Adapter Pack 2016 | Microsoft Docs"
description: Typical or custom installation of BAP 2016, 32-bit vs 64-bit, install in silent mode 
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f3e1717-8063-4460-bfdc-a933cd58a5c1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install the BizTalk Adapter Pack 2016
Install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in the following two ways:  

-   **In interactive mode**: Run the setup wizard  

-   **In silent mode**: Use the command line  

> [!IMPORTANT]
> - You must have administrative privileges on the computer where you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], irrespective of whether you are installing using the wizard, or the command line.  
> - Be sure all the [software prerequisites](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) are installed before installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

## Typical vs custom installation  
Lists the installation types, and the features that are installed with each option:  

- The **Typical** and **Complete** options install all the adapters, with the associated data providers. You do not have the option of choosing a specific adapter to install.  

- The **Custom** option installs one or more adapters, with the associated data providers. You can choose which adapters to install. If you choose to install a data provider, you must also install the corresponding adapter. However, you can install an adapter without installing the corresponding data provider. Do this by expanding the **ADO Providers** node, and then selecting the providers that you don't want to install. See **Install using the setup wizard** (in this topic).  

   For example, if you install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], you must also install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]. However, you can install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] without installing the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  

## 32-bit and 64-bit install scenarios
 With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be used for: 

- [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] design time (when generating metadata for operations on LOB applications)

- BizTalk Server Administration console design time (for creating physical ports)

  > [!NOTE]
  >  BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.  

- BizTalk run time (when sending and receiving messages from LOB applications)

You can use a single computer for all these taks, or use different computers. Because both [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on the computer where you complete the design-time tasks. 

### 32-bit install scenario
Install the following software on each computer. If you are using a single computer, all the software must be installed on that computer. 

1. Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]
2. Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].
3. Install 32-bit LOB client and other required DLLs.  

### 64-bit install scenarios

|                                                                                                                 For Visual Studio design time                                                                                                                  |                                                                                                                  For BizTalk MMC design time                                                                                                                   |                                                                                                                                                                                                                                                                                                         For BizTalk run time                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time                                                                                                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 64-bit LOB client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 64-bit LOB client and other required DLLs.<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. |

> [!NOTE]
>  On any computer where you want to do design-time tasks, using either [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

## Install using the setup wizard  
Steps to install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode.  

1. Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**.  

2. Select **Install Microsoft BizTalk Adapters**. In the next window, any missing prerequisite programs are listed. If any are missing, then select the missing program, and setup installs it for you. 

   For example, select **Step 2: Install Microsoft BizTalk Adapter Pack** or **Step 3: Install Microsoft BizTalk Adapter Pack (x64)**.  

   > [!NOTE]
   >  If you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on a virtual machine, the setup wizard may display a message that it's checking for available disk space. If this message appears to hang or just sit there, then we recommend you **Install in silent mode** (in this topic).  

3. On the Welcome screen, select **Next**.  

4. Accept the end-user license agreement (EULA), and then select **Next**.  

5. In **Choose Setup Type**:  

   -   To install the most common features, select **Typical**.  

   -   To select the adapters you want to install, select **Custom**, and then proceed to the next step.  

   -   To install all the features, select **Complete**.  

       > [!IMPORTANT]
       >  To install only the adapter that you use to interface with your enterprise application, select the **Custom** installation.  

6. **Required** only if you chose the Custom installation. If you chose the **Typical** or **Complete** installation, then skip this step, and go to step 7.  

    1.  In **Custom Setup**, expand **Base Adapters** to see the available adapters.  

    2.  For the adapters that you don't want, select the icon next to the adapter, and then select **Entire feature will be unavailable**.  

    3.  Expand **ADO Providers**, and then select the providers that you don't want to install.  

    4.  Select **Next**.  

7. Select **Install**.  

8. In **Customer Experience Improvement Program**, you can choose to enroll. If you enroll, you can share the following data with Microsoft:  

   - Data related to the computer hardware on which you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

   - Data related to the enterprise application versions you are using with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

     [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) provides more information.  

     Select **OK**. 

   > [!NOTE]
   >  You can always change this setting by running the Setup in Repair mode from **Programs**.  

9. Select **Finish**.  

<a name="BKMK_SilentInst"></a>   
## Install in silent mode  
 Use the **msiexec** command to do a silent installation. As part of the msiexec command, enter the individual components that you want to install. The following table lists the values for each component in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Use these values to install (or remove) specific components. To install (or remove) more than one component, you can use a combination of these values separated by a comma.  


|                                    Component name                                    |                                                                Corresponding value for command-line properties                                                                 |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]        |                                                                                   DbFeature                                                                                    |
| [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)] |                                                                                OracleEBSFeature                                                                                |
|           [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]           |                                                                             SapBaseAdapterFeature                                                                              |
|        [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]        |                                                                            SiebelBaseAdapterFeature                                                                            |
|            [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]            |                                                                                   SqlFeature                                                                                   |
|        [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]        |     SapAdoFeature<br /><br /> **Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] also.      |
|     [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]     | SiebelAdoFeature<br /><br /> **Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] also. |
|                                    All components                                    |                                                                                      ALL                                                                                       |

> [!IMPORTANT]
>  The feature names are case-sensitive.  

 The following steps show you how to complete a silent installation of [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] for different components.  

### Silent mode steps

1. Open a command prompt, and go to the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] root in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  

2. Run the following commands based on what you want to install:  

   > [!NOTE]
   >  To do silent installation on an x64-based platform, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi` in the following commands.  

   - To perform a complete installation, which installs all the adapters including the .NET Framework Data Providers, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
     ```  

   - To install only the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
     ```  

   - To install only the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
     ```  

   - To install only the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
     ```  

   - To install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] along with [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
     ```  

   - To install only the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
     ```  

   - To install the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] along with [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
     ```  

   - To install only the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
     ```  

   - To install all the base adapters, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
     ```  

   - To install the two .NET Framework Data Providers, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
     ```  

   - Any type of custom installation by separating the components by a comma. For example, to install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] with the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], and the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
     ```  

   - You can also opt to enroll for CEIP as part of the silent installation. Type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
     ```  

      By default the option is false. 

     > [!IMPORTANT]
     >  While installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Evaluation version in silent mode, the default option for CEIP is true.  

     For more information about the **msiexec** command, type `msiexec` on the command line, and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).

## Known install issue
For a comprehensive list of installation-related issues, refer to **Troubleshooting** topics for each adapter.  

**Running setup on a 64-bit computer may throw an error while accessing schema file**  

The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup throws an error while accessing the Microsoft.Adapters.*\<AdapterName\>*_schema.xml file, but proceeds with the adapter installation.  

**Cause**  

If both 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] are installed on the same computer, the target schema file used by both is the same. As a result, the file installed by the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] might be in use by IIS when the 64-bit installer tries to access it.  

**Resolution**  

Manually copy the Microsoft.Adapters.*\<AdapterName\>*_schema.xml file from *C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas* to *C:\Windows\System32\inetsrv\config\schema*. 

## Next step
[Post installation steps](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)