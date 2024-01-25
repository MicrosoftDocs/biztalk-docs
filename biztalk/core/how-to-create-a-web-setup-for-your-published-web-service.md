---
description: "Learn more about: How to Create a Web Setup for Your Published Web Service"
title: "How to Create a Web Setup for Your Published Web Service"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Create a Web Setup for Your Published Web Service
You can create an installation package to facilitate setting up your Web service in a production environment. This produces an .MSI file.

### To create an installation package to produce an .MSI file using Visual Studio

1. Open your published ASP.NET Web service project.

2. In Solution Explorer, right-click the solution node, click **Add**, and then click **New Project**.

3. In the **Add New Project** dialog box, in the **Project Types** area, expand **Other Project Types**, expand **Setup and Deployment Projects**, and then select **Visual Studio Installer**. In the **Templates** area, select **Web Setup Project**.

4. In the **Name** text box, type a name for the Web Setup Project. You can use the same name as the ASP.NET Web Service project and add "_Setup" as a suffix and then click **OK**.

5. In Solution Explorer, right-click the newly created Web setup project node, and point to **View**, and then click **File System**.

6. In the **File System** window, right-click the **Web Application Folder** node and point to **Add**, then click **Project Output**.

7. In the **Add Project Output Group** dialog box, select **Primary Output** and **Content Files** from the ASP.NET Web Service project and then click **OK**.

8. In Solution Explorer, expand the **Detected Dependencies** node under the Web setup project.

9. Select all dependencies. In the **Properties** window, set the **Exclude** property to **True**.

10. Build your Web setup project.

    > [!NOTE]
    >  For more information about creating Web setup projects, see "How to Create or Add a Web Setup Project" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [https://go.microsoft.com/fwlink/?LinkId=62268](/previous-versions/visualstudio/visual-studio-2010/19x10e5c(v=vs.100)).

## See Also
 [Deploying Published Web Services on a Non-Visual Studio Computer](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)