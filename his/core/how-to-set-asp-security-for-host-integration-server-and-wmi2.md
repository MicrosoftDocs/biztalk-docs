---
title: "How to Set ASP Security for Host Integration Server and WMI2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30e280ad-3f8b-497e-a5ef-47235182770e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Set ASP Security for Host Integration Server and WMI
WMI scripting using Active Server Pages (ASP) is enabled automatically on Windows. For the correct security setting for ASP on Windows, it is recommended that you set **Anonymous Authentication** to **Off** and enable **Integrated Windows Authentication** in the Internet Information Services (IIS) configuration for directories with ASP files used with Host Integration Server. To access Host Integration Server configuration and status information, an application or user must have the appropriate administrative rights, which are not available with anonymous authentication. Use the following procedure on Windows to correctly configure security using ASP.  
  
### To configure security using ASP  
  
1. To open IIS, click **Start**, point to **Administrative Tools**, point to **Services**, and then click **IIS Admin Service**, or click **Start**, point to **Settings**, click **Control Panel**, click **Administrative Tools**, click **Services**, and then click **IIS Admin Service**).  
  
2. Move to the directory where the ASP files reside.  
  
3. Right-click the directory, and then click **Properties**.  
  
4. When the next dialog box appears, on the **Directory Security** tab, in the **Anonymous Authentication** section, click **Edit**.  
  
5. When the next dialog box appears, clear the **Anonymous Authentication** check box, select **Integrated Windows Authentication**, and then click **OK** to save these settings.  
  
   This sets that particular directory to use **Integrated Windows Authentication** instead of **Anonymous Authentication** without affecting any of your other directories. If there are other ASP files that require or allow **Anonymous Authentication** you may want to create a new directory in which you can turn off **Anonymous Authentication** and store the WMI ASPs there. Any script that calls **ExecMethod** from an ASP page should be set up to use **Integrated Windows Authentication** to verify the user trying to run the script.  
  
   Additionally, when using a "REFRESH" variable on a Web page and the page is being used to start and stop SNA service through ASP scripting, the Web browser client (Internet Explorer, for example) should set the **Every visit to the page** option, as shown in the following procedure.  
  
#### To use a Web browser client to start and stop SNA services through ASP scripting  
  
1. Click **Start**, point to **Programs**, and then click **Internet Explorer**.  
  
2. In Internet Explorer, on the **Tools** menu, click **Internet Options**.  
  
3. In the **Internet Options** dialog box, on the **General** tab, in the **Temporary Internet file** section, click **Settings**.  
  
4. In the **Settings** dialog box, in the **Check for newer versions of stored pages** section, make sure that the option **Every visit to the page** is selected.  
  
5. Click **OK**.  
  
   If this change is not made on the Web browser client, some ASP scripts do not run correctly because Internet Explorer is caching older results.