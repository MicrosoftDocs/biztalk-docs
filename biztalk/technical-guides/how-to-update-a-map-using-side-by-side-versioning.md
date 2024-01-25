---
description: "Learn more about: How to Update a Map Using Side-by-Side Versioning"
title: "How to Update a Map Using Side-by-Side Versioning"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Update a Map Using Side-by-Side Versioning
Some BizTalk artifacts, such as maps, are chosen by fully-qualified strong name (FQSN), in which case the bindings include the version used. This allows two or more maps to coexist side by side in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. As a result, you can select one of the maps for inbound mapping in the receive location properties or outbound mapping in the send port properties.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.  
  
### To add a second map side by side to an existing map  
  
1.  Open Visual Studio, and then open the project containing the map.  
  
2.  Open the map in the assembly, and make a code change to the map.  
  
    > [!NOTE]  
    >  If you call a map from an orchestration, and the map reference is hard-coded, you may need to make code changes to the orchestration itself.  
  
3.  Change the version number of the assembly:  
  
    1.  In Solution Explorer, right-click the BizTalk project, and then click **Properties**.  
  
    2.  In the **Project Designer**, click the **Application** tab.  
  
    3.  In the right pane, click **Assembly Information**.  
  
    4.  In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to change the assembly version number. You should change only the major or minor version number. The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0).  
  
    5.  Click **OK** to close the **Assembly Information** dialog box.  
  
4.  Compile the assembly.  
  
5.  Deploy the assembly to the group (and all computers).  
  
## Modifying a Map to Reflect Updated Version Numbers  
 .NET assemblies can be invoked from within a map by using the Scripting functoid. This provides a great deal of flexibility and enables the developer to solve many different custom mapping problems. It also imposes a unique constraint on the map—it must internally reference not only the assembly type name but also the full assembly version number being invoked. As a consequence, if the version number of the assembly called by the map changes, all of the links that reference the assembly will break.  
  
 To avoid this issue we recommend that if assemblies are required to be called from a map, a specific assembly is created to hold only map functionality and that the assembly version number of this assembly is fixed. In this way, other helper functions can have the assembly version updated without breaking the maps.  
  
 If an assembly referenced from a map is changed after map development then consider updating the map file outside of the Map Editor to reflect the updated version numbers.  
  
#### To modify a map file to reflect updated version numbers  
  
1.  Using the **Start** menu, open **Notepad**.  
  
2.  In **Notepad**, on the **File** menu, click **Open**. In the **Open** dialog box, select the map file you want to modify, and then click **Open**.  
  
3.  On the **Edit** menu, click **Find**. In the **Find** dialog box, enter **Assembly=**, and then click **Find Next**.  
  
4.  If there is a script reference to an external assembly, Notepad should find an XML element like the following:  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=  
    <token>  
    " Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
5.  Update the version number. If there are multiple instances, use **Replace** on the **Edit** menu.  
  
6.  Save the file.  
  
    > [!NOTE]  
    >  You can now open the map using the Map Editor.
