---
title: Install AppFabric Connect for Services
description: Learn about installing AppFabric Connect for Services in BizTalk Server.
ms.service: biztalk-server
ms.topic: how-to
ms.date: 06/08/2017
---

# Install AppFabric Connect for Services in BizTalk Server

This guide provides instructions on how to install BizTalk Server 2010 Feature Pack (October 2010). The feature pack installs BizTalk Server 2010 AppFabric Connect for Services feature that provides enhancements to the **BizTalk WCF Service Publishing Wizard** and the **WCF Adapter Service Development Wizard**. After you have installed the feature pack, you will be able to extend the reach of your on-premises BizTalk Server artifacts or LOB applications to cloud by adding a Windows Azure AppFabric Service Bus endpoint.

## Prerequisites
 BizTalk Server 2010 Feature Pack provides enhancements to the BizTalk WCF Service Publishing Wizard and the WCF Adapter Service Development Wizard. While the BizTalk WCF Service Publishing Wizard is available with BizTalk Server 2010 Developer Tools, WCF Adapter Service Development Wizard is available with BizTalk Adapter Pack 2010. So, before you install the feature pack, you must have either BizTalk Server 2010 Developer Tools or BizTalk Adapter Pack 2010 or both installed. If you have only one of these installed, only the wizard relevant to the parent product installation will be updated as part of the feature pack installation.

 Other than this, there are some prerequisites for using these wizards. The complete list of prerequisites for each wizard is listed in the topics describing how to use the wizards. The links to the topics are provided under [Using AppFabric Connect for Services](../technical-guides/installing-appfabric-connect-for-services.md#BKMK_Using).

## Installing BizTalk Server 2010 Feature Pack
 Perform the following steps to install AppFabric Connect for Services:

#### To install the feature pack

1.  Download the AppFabric Connect for Services installable. Run the self-extracting BizTalkServer2010_FeaturePack.exe file to launch the feature pack installer.

2.  On the **Welcome** page, click **Next**.

3.  Accept the terms for licensing and then click **Next** and then in the following screen, click **Next** again.

4.  After the wizard completes the feature pack installation, click **Finish**.

##  <a name="BKMK_Using"></a> Using AppFabric Connect for Services
 After installing AppFabric Connect for Services, you can do the following:

-   Use the **BizTalk WCF Service Publishing Wizard** to expose BizTalk artifacts (orchestration, schema, etc.) as WCF services with a relay endpoint on the Azure AppFabric Service Bus. For more information, see [https://go.microsoft.com/fwlink/?LinkId=204700](https://go.microsoft.com/fwlink/?LinkId=204700).

-   Use the **WCF Adapter Service Development Wizard** to expose operations on LOB applications as WCF services with a relay endpoint on the Azure AppFabric Service Bus. For more information, see [https://go.microsoft.com/fwlink/?LinkId=204699](https://go.microsoft.com/fwlink/?LinkId=204699).

## Uninstalling BizTalk Server 2010 Feature Pack
 This section provides instructions on uninstalling AppFabric Connect for Services.

#### To uninstall the feature pack

1.  Open Windows Update, click **View update history**, and then click **Installed Updates**.

2.  From the list of installed updates, under **BizTalk Server 2010** category, right-click **BizTalk Server 2010 Feature Pack (October 2010) LDR**, and then select **Uninstall**. In the dialog box confirming whether you want to uninstall the feature pack, click **Yes**.

3.  Refresh the list to verify whether the feature pack is uninstalled.

## Copyright
 This document supports a preliminary release of a software product that may be changed substantially prior to final commercial release.  This document is provided for informational purposes only and Microsoft makes no warranties, either express or implied, in this document.  Information in this document, including URL and other Internet Web site references, is subject to change without notice.  The entire risk of the use or the results from the use of this document remains with the user.  Unless otherwise noted, the companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted in examples herein are fictitious.  No association with any real company, organization, product, domain name, e-mail address, logo, person, place, or event is intended or should be inferred.  Complying with all applicable copyright laws is the responsibility of the user.  Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

 Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document.  Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

 © 2010 Microsoft Corporation.  All rights reserved.

 Microsoft, Active Directory, ActiveX, BizTalk, Excel, InfoPath, JScript, IntelliSense, Internet Explorer, MSDN, Outlook, PivotChart, PivotTable, PowerPoint, SharePoint, Tahoma, Visio, Visual Basic, Visual C++, Visual C#, Visual SourceSafe, Visual Studio, Win32, Windows, Windows NT, Windows PowerShell, Windows Server, Windows Server System, and Windows Server are trademarks of the Microsoft group of companies.

 SAP, R/3, mySAP, mySAP.com, xApps, xApp, SAP NetWeaver, and other SAP products and services mentioned herein as well as their respective logos are trademarks or registered trademarks of SAP AG in Germany and in several other countries/regions all over the world. All other product and service names mentioned are the trademarks of their respective companies. Data contained in this document serves informational purposes only. National/regional product specifications may vary.

 All other trademarks are property of their respective owners.
