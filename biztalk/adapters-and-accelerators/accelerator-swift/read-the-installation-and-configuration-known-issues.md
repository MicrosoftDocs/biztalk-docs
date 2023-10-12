---
description: "Learn more about: Read the installation and configuration known issues"
title: "Read the installation and configuration known issues"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Read the installation and configuration known issues
  
## Installing over Terminal Server creates log files in a different folder  
 When you install A4SWIFT over a Terminal Server connection, the A4SWIFT Setup program creates the setup and configuration log files in the *\<drive\>*:\Documents and Settings\\*\<user name\>*\Local Settings folder. Normally, the Setup program creates these files in the *\<drive\>*:\Documents and Settings\\*\<user name\>*\Local Settings\temp folder. You can review these log files to ensure that your computers are set up and configured properly.  
  
## Silent installation is not recommended  
 A silent installation is supported by the A4SWIFT Setup program, but is not recommended because of the complexity of the additional configuration steps that are required.  
  
## A4SWIFT setup runs with the /InstallPlatform argument that overwrites DLLs for VisualStudio.Net  
 The A4SWIFT setup program always runs with the /InstallPlatform argument. As a result, A4SWIFT setup always installs msvcr71.dll, mfc71u.dll, msvcp71.dll, and atl71.dll, which are required for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. A4SWIFT setup installs these DLL files into the %WINDIR%\System32 folder, whether the DLLs have been previously installed or not.  
  
## Canceling A4SWIFT configuration will fail  
 Clicking **Cancel** during A4SWIFT configuration will not cancel configuration. The configuration process will continue until complete.  
  
## After unconfiguring A4SWIFT, you cannot reconfigure in the same instance of the Configuration console  
 If you unconfigure A4SWIFT, or a component of A4SWIFT, you cannot reconfigure A4SWIFT or its component without first closing the A4SWIFT Configuration console, and then reopening it. If you do not do so, certain fields of the Configuration console will be grayed out, and you will not be able to select values for them.  
  
## Configuration of a Web Components-only installation will succeed even if no A4SWIFT database exists  
 If you perform a custom installation that installs only the Web components for Message Repair and New Submission feature, and then run the Microsoft BizTalk Accelerator for SWIFT Configuration Wizard, the Configuration program will complete successfully even though there is no A4SWIFT database.  
  
 An A4SWIFT database will be shown in the **Web Components for Message Repair and New Submission** pane of the A4SWIFT Configuration dialog box, even though that database does not exist. A warning will be displayed for the A4SWIFT database in the Data stores pane, but that warning will not prevent the configuration process from proceeding.  
  
## Upgrade process does not create a new root folder  
 The upgrade process updates A4SWIFT files in the existing *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for A4SWIFT 2.3/3.0 folder. It does not create a new folder for the upgraded files, nor does it change the name of the existing folder to *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT.  
  
## Canceling Setup during an upgrade for A4SWIFT may leave your system in an unknown state  
 In some scenarios, clicking the **Cancel** button during an upgrade may leave files, assemblies, BizTalk Server artifacts, and registry keys intact after Setup has finished its rollback.  
  
 You can manually remove all items without any problems.  
  
## Download the A4SWIFT setup exe file from the Web into a temp folder  
 If you are going to install A4SWIFT from a self-extracting executable file that you download from the Web, be sure to download that file into a temp folder. Do not download the file into the BizTalk Server root folder (\Program Files\Microsoft BizTalk Server \<*your version*\>).  
  
 If you run the exe file from the BizTalk Server root folder, it runs the BizTalk Server setup wizard, not the A4SWIFT setup wizard.  
  
## Installing A4SWIFT in a location other than the default requires changes to the BREDeployment.exe.config file  
 If you install BizTalk Accelerator for SWIFT in a path other than the default path of %programfiles%\Microsoft BizTalk Accelerator for SWIFT, you must edit the BREDeployment.exe.config file in the SDK\Tools subdirectory of the product to reflect the correct paths for the BasePoliciesDirectory, SchemasDirectory, and VocabularyDirectory.  
  
 You must make this change before attempting to deploy any of the rules associated with the SWIFT schemas included in your projects to successfully deploy the relevant rules and vocabulary.  
  
## Message repair is not supported for certain batched message scenarios  
 A4SWIFT supports message repair only for fragmentation batching scenarios. In these scenarios, only the interchange portion of batched messages can be repaired.  
  
## You cannot submit a fixed unparsed message from a MRSR site library named anything other than Unparsed  
 When you try to submit an unparsed message that you have fixed from a MRSR site document library that is not named "Unparsed," the operation fails because A4SWIFT cannot successfully submit a message from a library that is not named "Unparsed."  
  
 If you have an existing "Unparsed" document library in MRSR site before you install the Message Repair and Reconciliation feature, A4SWIFT Setup creates a library for unparsed messages entitled "Unparsed" with a suffix.  
  
 When A4SWIFT receives a message that it cannot parse, it routes the message to the library that Setup created. However, when you try to submit a message from that library, the operation fails.  
  
 This issue would generally occur if you uninstal A4SWIFT and do not remove the “Unparsed” document library from the MRSR site.  When reinstalling SWIFT under these circumstances, the setup creates a new document library with name “Unparsed” with a suffix.”  
  
 To resolve this issue, follow this procedure:  
  
#### To name a library "Unparsed" in order to submit unparsed messages  
  
1.  Remove the Message Repair and Reconciliation feature.  
  
2.  Manually delete the Unparsed library. This does not get deleted when uninstalling A4SWIFT.  
  
3.  Reinstall Message Repair and Reconciliation. During the reinstallation, the document library will be created with the name “Unparsed” and you can submit the fixed unparsed messages through this document library.  
  
## BREDeployment utility cannot deploy or undeploy policies if A4SWIFT vocabularies are not correctly configured  
 If you try to undeploy A4SWIFT Business Rule Engine policies by using the BREDeployment.exe tool, and the BREDeployment.exe configuration file does not point to the correct vocabulary file location, then the tool may report an error. You will have this problem if you change the location in the BREDeployment.exe configuration file and the new location does not contain the vocabulary files. The error informs you that the vocabularies were not found and the configuration stops deploying and/or undeploying policies.  
  
 To resolve this issue, use the standard **Business Rules Engine Deployment Wizard**. UI details are [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-swift/known-issues5.md)
