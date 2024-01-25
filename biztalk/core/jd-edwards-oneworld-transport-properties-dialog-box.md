---
description: "Learn more about: JD Edwards OneWorld Transport Properties Dialog Box"
title: "JD Edwards OneWorld Transport Properties Dialog Box"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "JDEOneWorld"
---
# JD Edwards OneWorld Transport Properties Dialog Box
Use the JD Edwards OneWorld Transport Properties dialog box to set the adapter-required properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Adapter Required Properties**||  
|Host|Type the name of the host server computer (for example, `actsvr1`).<br /><br /> --or--<br /><br /> Type the IP address of the computer (for example, `123.456.0.789`).|  
|JAVA_HOME|Type the complete path to your JDK installation.|  
|JDEdwards Environment|Type the name of an environment in JD Edwards OneWorld (for example, `DV7333`).<br /><br /> DV7333 is a common name for the development environment, PY7333 is common for the prototype environment, and PD7333 is common for the production environment.|  
|JDEdwards JAR files|Enter the complete path and file name for each of the JAR files:<br /><br /> -   Connector.jar<br />-   Kernel.jar<br />-   JDEJAccess.jar<br />-   BTSLIBInterop.jar<br /><br /> Each jar file must be separated with a semi-colon (;) and no space (for example, `<c:>\Connector.jar;<c:>\Kernel.jar;`).|  
|Password|Type a user password. If you do not use Single Sign-On (SSO), you must set credential parameters for BizTalk Adapter for JDEdwards OneWorld to access the server system. The password corresponds to the user name. The password determines the privileges you are granted when accessing the database.|  
|Port|Type the numerical identifier of the send or receive port (for example, `6009`).|  
|User name|Type the name of the user, and then click **OK**.|  
|Max Concurrent Calls|Type a numeric value for the **Max Concurrent Calls**. This number represents the maximum number of concurrent calls, for example, **10**.<br /><br /> The default value for this field is **5**, meaning no protection occurs.|  
|Refresh Agent|Select **Yes** for the **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.<br /><br /> For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.|  
|Affiliate Application|Select the affiliate application from the list only if you are using SSO.|  
|Use SSO|Select **Yes** if you are using SSO; a password is not required in this case.|  
  
## See Also  
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Creating Affiliate Applications](../core/creating-affiliate-applications3.md)   
 [UI Reference for BizTalk Adapter for JDE OneWorld](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md)
