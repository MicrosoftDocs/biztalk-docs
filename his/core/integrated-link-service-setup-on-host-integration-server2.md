---
title: "Integrated Link Service Setup on Host Integration Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f75c0ab-fc00-4c42-bc95-3dd6cbec9aaf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Integrated Link Service Setup on Host Integration Server
In Host Integration Server, the SNA Manager supports installation and configuration of link services. Host Integration Server uses the Microsoft System Installer (MSI) and MSI packages for the installation of the Host Integration Server software. Link services from independent hardware vendors (IHVs) are not included in the main Host Integration Server MSI packages. IHV link services are installed using a separate IHV-provided MSI package. For an example of this process, install the DLC, 802.2, or IBM Synchronous Data Link Control (SDLC) link service in Host Integration Server.  
  
 IHV MSI Packages contain two types of features:  
  
- Features that can be installed and used independently of Host Integration Server.  
  
- Features that require Host Integration Server to function.  
  
  Features that can be installed and used independently of Host Integration Server include drivers, utilities, and applications that can run without Host Integration Server support. These features should be represented in the package as one or more features in the MSI Select Features dialog box. (For more information, see the Generic Link Service sample feature "Generic Link Service" from the Generic.msi Featuretable.) Generic.msi can be found in the Host Integration Server SDK.  
  
  Features that require Host Integration Server include drivers, utilities, and applications that require Host Integration Server to function. These features should be represented in the package as one or more features in the MSI Select Features dialog box. These features should be hidden if Host Integration Server is not installed on the computer. (For more information, see the Generic Link Service sample feature "Host Integration Server Support" from the Generic.msi feature table.)  
  
  Properties can be equated to a variable (either global or local) in a high-level programming language such as C or C++. Properties can be used as a placeholder for informational text, or as values used during an installation. (For more information, see the property SERVER_INSTALLED in the custom action source code GenSet.cpp, and the Condition table entry in the Generic.msi package.)  
  
  Custom Actions provide a method of extending the capabilities of MSI. Functions not supported in MSI, can be custom written, and invoked from within a sequence table or directly from a dialog control event. (For more information, see the Custom Actions SetHISPath and GetHISData in the GenSet.cpp source file.)  
  
  Launch Conditions provide a method of preventing an install from launching. The sample MSI package included with the Host Integration Server SDK does not use a launch condition, however, if your package requires Host Integration Server to be installed for your features to function, you should include a launch condition that fails the installation if Host Integration Server is not detected.  
  
  The Condition table provides a method of controlling the layout of the features listed in the select feature dialog box. The sample MSI package uses the Condition table to hide the "Host Integration Server Support" if Host Integration Server is not detected in the installation.  
  
  For Host Integration Server to control the installed state of IHV features that require Host Integration Server to be installed, the following registry keys must be included in the package for each separate feature which requires Host Integration Server to be installed.  
  
```  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SnaBase\IHVSupport\<ihv key>  
<feature table entry 1> : REG_SZ : <product code 1>  
<feature table entry 2> : REG_SZ : <product code 2>  
.  
.  
.  
<feature table entry n> : REG_SZ : <product code n>  
```  
  
 Where:  
  
 \<feature table entry x> specifies an entry in the feature table (not title).  
  
 \<product code x> specifies the package product code.  
  
 Note that feature table entries must be unique. Product codes may or may not be unique depending on the number of packages provided by an IHV. One package may have several Host Integration Server dependent features and therefore should list each feature separately.  
  
 These registry keys should be installed by the feature rather than globally by the package.  
  
```  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SnaBase\LinkServicesInstalled  
<Link Service Name> : REG_SZ : <Link Service Configuration Dll name>  
```  
  
 Target paths specify a directory where files will be installed. An MSI package will contain one or more target paths.  
  
 The sample package contains two features:  
  
- Generic Link Service  
  
- Host Integration Server Support  
  
  The Generic Link Service is not dependent on Host Integration Server. This feature installs the following:  
  
- gencfg.exe into the \<Generic Link Service> directory.  
  
- generic.sys driver into the %windir%\system32\drivers directory.  
  
- generic.inf into the %windir%\inf directory  
  
  Host Integration Server Support is dependent on Host Integration Server. This feature installs the following:  
  
- gendtct.dll into the HIS\system directory.  
  
- generic.dll into the HIS\system\hwsetup\i386 directory.  
  
  This feature contains the following entry in the condition table to hide the feature if Host Integration Server is not detected  
  
```  
HIS_RELATED_FEATURE  0  SERVER_INSTALLED="NO"  
```  
  
 See dialog snapshots later in this topic for layout of features with and without Host Integration Server installed:  
  
 Adds:  
  
```  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SnaBase\LinkServicesInstalled  
Generic Link Service : REG_SZ : GENERIC.DLL  
  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SnaBase\IHVSupport\GenericLinkService  
HIS_RELATED_FEATURE : REG_SZ : {FDF11E0E-3BFF-4B0F-89BD-E4E1FB979E4D}  
```  
  
 The sample package uses one custom action DLL with two entry points:  
  
```  
SetHISPath  
GetHISData  
```  
  
 The **SetHISPath** entry sets the target path to the Host Integration Server installation directory.  
  
 The **GetHISData** entry sets the MSI property SERVER_INSTALLED to "YES" if Host Integration Server is installed and sets the MSI property SERVER_INSTALLED to "NO" if Host Integration Server is not installed.  
  
 The sample contains two target paths:  
  
```  
INSTALLDIR  
INSTALLDIR1  
```  
  
 The INSTALLDIR target path specifies the installation directory for the features that are not dependent on Host Integration Server. It can be set using the **browse** button in the **Select Features** dialog box when the Generic Link Service feature is currently selected.  
  
 The INSTALLDIR1 target path specifies the directory where Host Integration Server is installed. This target path is set by the custom action SetHISPath.  
  
 The IHVUtil.exe tool can be used to verify the Host Integration Server dependent interfaces. If the tool is launched after the IHV package is installed, all Host Integration Server dependent features should show up in the dialog box. Executing Remove from the dialog box should remove the Host Integration Server dependent feature as well as remove it from the dialog box.  
  
 Note that the sample provided can also be tested using the SNA Manager. While the sample does not actually function, it will appear as an installed link service.  
  
## In This Section  
 [Integrated Link Service Configuration and Reconfiguration on Host Integration Server](../core/2d8129c3-3859-49e8-9c1d-a8aef89f58a4.md)  
  
 [Constructing an Integrated Link Service DLL on Host Integration Server](../core/constructing-an-integrated-link-service-dll-on-host-integration-server2.md)