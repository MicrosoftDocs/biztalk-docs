---
title: Viewing the WMI Core Server Classes in CIM Studio
TOCTitle: Viewing the WMI Core Server Classes in CIM Studio
ms:assetid: da9a0b3d-47c5-404a-b9a9-ed4298178001
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561401(v=BTS.80)
ms:contentKeyID: 51531758
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Viewing the WMI Core Server Classes in CIM Studio

 

The following figure shows the class hierarchy of the WMI Core classes, as displayed in CIM Studio.

![](images/Aa561401.2443b144-083c-413e-8878-4d1fe1cf8aee(BTS.80).jpeg)  
Depicts the class hierarchy for WMI Core classes.

#### To view documentation for WMI Classes using CIM Studio

1.  Install CIM Studio, part of the Windows Management Instrumentation (WMI) SDK 1.5. The WMI SDK is available for download at [http://go.microsoft.com/fwlink/?LinkId=93373](http://go.microsoft.com/fwlink/?linkid=93373).

2.  To download the minimal requirements for CIM Studio, in the WMI SDK Installation Wizard, on the Components screen, select **Applications** only, uncheck the other options.

3.  Once the WMI SDK is installed, click **Start**, click **All Programs**, point to **WMI Tools**, and then click **WMI CIM Studio**.

4.  In the **Connect to namespace** dialog box, type **root\\MicrosoftBizTalkServer**, and then click **OK**.

5.  In the WMI CIM Studio Login dialog box, click Options to change the impersonation level, the authentication level, authority, or to enable all privileges, and configure the appropriate settings. For more information, click the help button on the dialog box.

6.  In the Windows Management Instrumentation Tools: WMI CIM Studio - Microsoft Internet Explorer window, in the right pane, expand the CIM\_ManagedSystemElement and CIM\_Setting folders until you reach the MSBTS\_\* classes.

7.  Click a class in the left pane, which displays a class view in the right pane, and then click the Help for class button, identified as a question mark in the top right corner of the screen to view descriptions for the members of the class.

#### To view documentation for WMI Classes using the MOF file

1.  Click Start, point to All Programs, point to Accessories, and then click Windows Explorer.

2.  In Windows Explorer, navigate to the BizTalk Server install directory, right-click BTSWMISchema.mof, in the **Windows** dialog box, select **Select the appropriate program from a list**, and then click **OK**.

3.  In the **Open With** dialog box, in Programs, select a text editor, such as **NotePad** or **Wordpad**, and then click **OK**.
    
    The BTSWMISchema.mof file is displayed in the text editor. The comments appear at the bottom of the text file.

## See Also

[Admin-WMI (BizTalk Server Samples Folder)](https://msdn.microsoft.com/library/aa559638\(v=bts.80\))

