---
description: "Learn more about: Publishing the MX Message Instance File (Creating New Messages)"
title: "Publishing the MX Message Instance File (Creating New Messages)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Publishing the MX Message Instance File (Creating New Messages)
**To publish the MX message instance file:**  

1. Go to output folder of the InfoPath form template generated in the previous step **..\\<MessageType\>\TemplateDS\InfoPath Form Template**.  

2. In Internet Explorer, open **http://localhost/sites/BASSite/New%20SWIFT%20MX%20Messages**.  

3. In New Swift MX Messages window, click **Upload**.  

4. In the Upload Document window, click **Browse**.  

5. In the Choose file dialog box, move to the output folder of the InfoPath form generated in the previous step **..\\<MessageType\>\TemplateDS\InfoPath Form Template**. Select the \<MessageType\>.xml file such as pacs.004.001.01.xml, and then click **Open**.  

6. In the Upload Document window, click **OK**.  

7. In the New SWIFT MX Messages: \<MessageType\> window, in the Namespace box, type `http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_<MessageType>`, and then click **OK**.
