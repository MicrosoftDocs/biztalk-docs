---
title: "SNANLS Dependencies2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bb2a609-8599-419c-af6d-51b89b6769f1
caps.latest.revision: 5
---
# SNANLS Dependencies
The only file required to support the SNA National Language Support (SNANLS) API on Windows operating systems is SNANLS.DLL. To link to this .dll, use the SNANLS.H header (located under the \SDK\INCLUDE subdirectory) and the SNANLS.LIB library file (located under the \SDK\LIB subdirectory) supplied with the [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] SDK. Note that individual Win32 NLS resource files must be installed in order to support the various languages and code pages on Windows.  
  
 The Win32 NLS files needed to support various languages are normally installed when the operating system is installed during Setup for Windows. If these files are not present on Windows, they may be installed using Regional and Language Options.  Click **Start**, then click **Control Panel**. Click **Regional and Language Options**, then click the **Advanced** tab. Select the appropriate settings from this dialog box.  
  
 The registry settings required to use specific NLS files are enabled on Windows when the operating system is installed. When you install the end-user client or Administrator clients from [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)], the registry settings required to use specific NLS files are automatically created.  
  
 The registry settings required for common EBCDIC code pages are listed in the following table.  
  
|File name|SNANLS display name|NLS code page|Host CCSID|Registry setting|  
|---------------|-------------------------|-------------------|----------------|----------------------|  
|c_037.nls|EBCDIC - U.S./ Canada|37|37|Value Name=37 Type=REG_SZ Data=c_037.nls|  
|c_500.nls|EBCDIC - International|500|500|Value Name=500 Type=REG_SZ Data=c_500.nls|  
|c_870.nls|EBCDIC - Multilingual/ ROECE (Latin-2)|870|870|Value Name=870 Type=REG_SZ Data=c_870.nls|  
|c_875.nls|EBCDIC - Greek (Modern)|875|875|Value Name=875 Type=REG_SZ Data=c_875.nls|  
|c_1026.nls|EBCDIC - Turkish (Latin-5)|1026|1026|Value Name=1026 Type=REG_SZ Data=c_1026.nls|  
|c_20273.nls|EBCDIC - Germany|20273|273|Value Name=20273 Type=REG_SZ Data=c_20273.nls|  
|c_20277.nls|EBCDIC - Denmark/ Norway|20277|277|Value Name=20277 Type=REG_SZ Data=c_20277.nls|  
|c_20278.nls|EBCDIC - Finland/ Sweden|20278|278|Value Name=20278 Type=REG_SZ Data=c_20278.nls|  
|c_20280.nls|EBCDIC - Italy|20280|280|Value Name=20280 Type=REG_SZ Data=c_20280.nls|  
|c_20284.nls|EBCDIC - Latin America/<br /><br /> Spain|20285|284|Value Name=20284 Type=REG_SZ Data=c_20284.nls|  
|c_20285.nls|EBCDIC - United Kingdom|20285|285|Value Name=20285 Type=REG_SZ Data=c_20285.nls|  
|c_20297.nls|EBCDIC - France|20297|297|Value Name=20297 Type=REG_SZ Data=c_20297.nls|  
|c_20420.nls|EBCDIC - Arabic|20420|420|Value Name=28596 Type=REG_SZ Data=c_20420.nls|  
|c_20423.nls|EBCDIC - Greek|20423|423|Value Name=20423 Type=REG_SZ Data=c_20423.nls|  
|c_20424.nls|EBCDIC - Hebrew|20424|424|Value Name=20424 Type=REG_SZ Data=c_20424.nls|  
|c_20838.nls|EBCDIC - Thai|20838|838|Value Name=20838 Type=REG_SZ Data=c_20838.nls|  
|c_20871.nls|EBCDIC - Icelandic|20871|871|Value Name=20871 Type=REG_SZ Data=c_20871.nls|  
|c_20880.nls|EBCDIC - Cyrillic (Russian)|20880|880|Value Name=20880 Type=REG_SZ Data=c_20880.nls|  
|c_20905.nls|EBCDIC - Turkish (Latin-3)|20905|905|Value Name=20905 Type=REG_SZ Data=c_20905.nls|  
|c_21025.nls|EBCDIC - Cyrillic (Serbian, Bulgarian)|21025|1025|Value Name=21025 Type=REG_SZ Data=c_21025.nls|  
  
> [!NOTE]
>  On Windows operating systems, the registry settings are located under the **HKEY_LOCAL_MACHINE** under the following sub key: SYSTEM\CurrentControlSet\Control\Nls\CodePage.