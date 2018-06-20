---
title: "Extending BTARN with a New PIP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BTARN, extending functionality"
  - "PIPs, extending BTARN"
  - "BTARN, PIPs"
ms.assetid: 3db5cd5c-031f-4451-9be5-4b5d6163c3b1
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extending BTARN with a New PIP
This topic describes how to extend [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] with a new Partner Interface Process (PIP) schema. This lets you add a schema based on a RosettaNet PIP when that PIP is not associated with any of the schemas installed by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program.  

 When you extend [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] with a new PIP, you deploy the new schema in its own assembly. You can also modify an existing schema that is deployed within the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIPs assembly. For more information, see [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  

### To extend BTARN with a new PIP  

1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  

2. At the command prompt, move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Utilities\Schema Generator.  

3. At the command prompt, type **CScript InstallDTD.vbs**, and then press **Enter**.  

   > [!NOTE]
   >  You will only have to perform steps 1 through 3 once after you install BizTalk Server.  

4. Start Visual Studio.  

5. On the **File** menu, point to **New**, and then click **Project**.  

6. In the New Project dialog box, select **BizTalk Projects** in the left pane, and then click **Empty BizTalk Server Project** in the right pane.  

7. Click **Browse** and point to the directory where you want to save your project.  

8. In the **Name** box, type a project name, such as **MyCustomPIP**, and then click **OK**.  

9. Start Visual Studio command prompt.  

10. At the command prompt, move to the location entered in step 7, type **sn -k \<project name.snk\>**, and then press **Enter**.  

11. In Solutions Explorer, right-click the project name, and then click **Properties**.  

12. In the **Property Pages** dialog box, click **Assembly** under **Common Properties** in the left pane.  

13. In the right pane, scroll down to **Strong Name**, click **Assembly Key File**, and then click the ellipsis button (...) in the right pane. Move to the location entered in step 7, and select the name of the .snk file created in step 10.  

14. In the Property Pages dialog box, expand **Configuration Properties**, and then click **Deployment**. In the right pane, click **Redeploy**, select `True`, and then click **OK**.  

15. In Solution Explorer, right-click the project name, point to **Add**, and then click **Existing Item**.  

16. In the **Add Existing Item** dialog box, move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\SDK\Schemas, select **xml.xsd**, then click **Add**.  

17. Download the PIP that you are going to extend RNPIPs with RosettaNet.org. For more information, see [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).  

18. In Solution Explorer, expand the project name, right-click **Reference**, and then click **Add Reference**.  

19. In the **Add Reference** dialog box, click **Browse**, and move to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk 2013 Accelerator for RosettaNet\Bin, and then select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**. Click **Open**, and then click **OK**.  

20. In Solution Explorer, right-click the project name, point to **Add**, and then click **Add Generated Items**.  

21. In the **Add Generated Items** dialog box, in the **Categories** pane, click **Generate Schemas**. In the **Templates** pane, click **Generate Schemas**, and then click **Add**.  

22. In the Generate Schemas dialog box, do the following:  


    |     Use this      |                                                                    To do this                                                                    |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Document type** |                                                              Select **DTD Schema**.                                                              |
    |  **Input File**   | Click **Browse**, move to the folder that contains the DTD file from RosettaNet.org, select the DTD file that you want, and then click **Open**. |


23. In the Generate Schemas dialog box, click **OK**.  

24. In Solution Explorer, double-click the .xsd file that you just imported.  

25. In BizTalk Editor, select the \<*Schema*\> node.  

26. In the Properties window, scroll down to **Document Type**. In the **Document Type** box, **PIP**\<*three-digit code*\>, for example, **PIP3A2**. In the **Document Version** box, type **v**\<*xx.xx*\> or **R**\<*xx.xx*\>, for example, **R01.02**. This version should be as documented in the RosettaNet PIP specification.  

27. In the Properties window, scroll down to **Root Reference**. Click **Root Reference**, and from the drop-down list, select the root node of the schema, for example, select **Pip3C5BillingStatementNotification**.  

28. In the Properties window, scroll up to **Target Namespace**. For **Target Namespace**, type <strong>http://schemas.microsoft.com/biztalk/btarn/2004/\<DTD file name\>.dtd</strong>, where the DTD file name is, for example, **3C5_MS_R01_00_BillingStatementNotification.dtd**.  

    > [!NOTE]
    >  This naming convention for the target namespace is required for BTARN. If you use another namespace convention, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not process PIP documents for schema validation.  
    > 
    > [!NOTE]
    >  The DTD file name in the target namespace property includes the version number of the PIP. This lets you use multiple versions of the same PIP code.  

29. In the Properties window, scroll up to **Imports**. Click the ellipsis button (...) next to **Imports**, and then click **Add**.  

30. In the **BizTalk Type Picker** dialog box, expand \<*Project Name*\>, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, expand **Schemas**, select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.BaseDataTypes**, click **OK**, and then click **OK** again.  

31. Right-click the project name, and then click **Deploy**.  

32. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

33. In BizTalk Administration Console, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, and then expand **Hosts**. Under **Host**, click **BizTalkServerApplication**.  

34. In the right pane, right-click the name of the host, and then click **Restart**.  

    > [!NOTE]
    >  After extending RNPIPs with a newly imported PIP, you must create the correct PIP configuration, and an agreement using that PIP, in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.  

## See Also  
 [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)   
 [Working with PIPs](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)