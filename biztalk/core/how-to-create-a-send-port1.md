---
description: "Learn how to create BizTalk Server send ports for JD Edwards EnterpriseOne."
title: "How to Create a Send Port1"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Create Send Ports

Use the following procedure to create BizTalk Server send ports for JD Edwards EnterpriseOne.  
  
### To create a send port  
  
1.  Right-click the Send Ports node.  
  
2.  Click **Add Send Port**.  
  
3.  In the **Create New Send Port** dialog box, select **Static Solicit-Response Port** from the **Specify the type of Send Port** list, and click **OK**.  
  
     The **Static Solicit-Response Send Port Properties** window opens.  
  
4.  Type a name for the send port, for example, `SSOSendToJDEEntOne`.  
  
5.  Click **Transport** in the left pane.  
  
6.  Click **Transport Type**, and select **JDEEntOne**.  
  
7.  Select the **Address (URI)**, and click the ellipsis (…) button.  
  
     The JD Edwards EnterpriseOne **Transport Properties** dialog box appears.  
  
8.  Type `myJDEEntOneSSO` for the **Logical System Name**.  
  
9. Select **Yes** for **Use SSO**.  
  
10. In the drop-down list, select the Single Sign-On (SSO) affiliate application that you created to represent the JD Edwards EnterpriseOne system.  
  
     Click **OK** to confirm the information you entered.  
  
## See Also
  
- [Creating Affiliate Applications](../core/creating-affiliate-applications4.md)   
- [Security in BizTalk Adapter for JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)
